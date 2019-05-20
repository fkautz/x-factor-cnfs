---
title: "III. Config"
date: 2018-10-09T15:10:51-07:00
draft: true
---
### Store config in the environment

A CNF's *config* is everything that is likely to vary between [deploys](./codebase) (staging, production, developer environments, etc).  This includes:

* Resource handles to the database, Memcached, and other [backing services](./backing-services)
* Credentials to external services such as databases or object storage
* Per-deploy values such as the canonical hostname for the deploy

CNFs sometimes store config as constants in the code.  This is a violation of X-factor, which requires **strict separation of config from code**.  Config varies substantially across deploys, code does not.

A litmus test for whether a CNF has all config correctly factored out of the code is whether the codebase could be made open source at any moment, without compromising any credentials.

Note that this definition of "config" does **not** include internal application config, such as [Fruit](https://github.com/google/fruit) for C++, [Guice](https://github.com/google/guice) for Java, or how [code modules are connected](http://docs.spring.io/spring/docs/current/spring-framework-reference/html/beans.html) in [Spring](http://spring.io/).  This type of config does not vary between deploys, and so is best done in the code.

Another approach to config is the use of config files which are not checked into revision control, such as a `config/` directory.  This is a huge improvement over using constants which are checked into the code repo, but still has weaknesses: it's easy to mistakenly check in a config file to the repo; there is a tendency for config files to be scattered about in different places and different formats, making it hard to see and manage all the config in one place.  Further, these formats tend to be language- or framework-specific.

**The X-factor CNF stores config in *environment variables*** (often shortened to *env vars* or *env*) or in *mounted data volumes* injected by the orchestrator.  Env vars are easy to change between deploys without changing any code; unlike config files, there is little chance of them being checked into the code repo accidentally; and unlike custom config files, or other config mechanisms such as Java System Properties, they are a language- and OS-agnostic standard.

Another aspect of config management is grouping.  Sometimes CNFs batch config into named groups (often called "environments") named after specific deploys, such as the `development`, `test`, and `production` environments in Rails.  This method does not scale cleanly: as more deploys of the app are created, new environment names are necessary, such as `staging` or `qa`.  As the project grows further, developers may add their own special environments like `joes-staging`, resulting in a combinatorial explosion of config which makes managing deploys of the CNF very brittle.

In a X-factor CNF, env vars are granular controls, each fully orthogonal to other env vars.  They are never grouped together as "environments", but instead are independently managed for each deploy.  This is a model that scales up smoothly as the CNF naturally expands into more deploys over its lifetime.
