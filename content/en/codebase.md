## I. Codebase
### One codebase tracked in revision control, many deploys

A X-factor CNF is always tracked in a version control system, such as [Git](http://git-scm.com/), [Mercurial](https://www.mercurial-scm.org/), or [Subversion](http://subversion.apache.org/).  A copy of the revision tracking database is known as a *code repository*, often shortened to *code repo* or just *repo*.

A *codebase* is any single repo (in a centralized revision control system like Subversion), or any set of repos who share a root commit (in a decentralized revision control system like Git).

![One codebase maps to many deploys](/images/codebase-deploys.png)

There is always a one-to-one correlation between the codebase and the CNF:

* If there are multiple codebases, it's not a CNF -- it's a distributed system.  Each component in a distributed system is a CNF, and each can individually comply with X-factor.
* Multiple CNFs sharing the same code is a violation of X-factor.  The solution here is to factor shared code into libraries which can be included through the [dependency manager](./dependencies).

There is only one codebase per CNF, but there will be many deploys of the CNF.  A *deploy* is a running instance of the CNF.  This is typically a production site, and one or more staging sites.  Additionally, every developer has a copy of the CNF running in their local development environment, each of which also qualifies as a deploy.

The codebase is the same across all deploys, although different versions may be active in each deploy.  For example, a developer has some commits not yet deployed to staging; staging has some commits not yet deployed to production.  But they all share the same codebase, thus making them identifiable as different deploys of the same CNF.

