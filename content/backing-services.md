---
title: "IV. Backing Cloud-Native Service"
date: 2018-10-09T15:10:51-07:00
draft: true
---

### Treat backing cloud-native services as attached resources

A *backing Cloud-Native service* is any service the CNF consumes over the orchestration-managed network as part of its normal operation.  Examples include other CNFs, datastores, messaging/queueing systems, SMTP services for outbound email, and caching systems.

Backing Cloud-Native services like the database are traditionally managed by the same systems administrators as the CNF's runtime deploy.  In addition to these locally-managed services, the CNF may also have services provided and managed by third parties.  Examples include other CNFs (such as a VPN), SMTP services (such as [Postmark](http://postmarkapp.com/)), metrics-gathering services (such as [Jaeger](https://www.jaegertracing.io/), [New Relic](http://newrelic.com/) or [Loggly](http://www.loggly.com/)), binary asset services (such as [Amazon S3](http://aws.amazon.com/s3/)), and even API-accessible consumer services (such as [Twitter](http://dev.twitter.com/).

**The code for a X-factor CNF makes no distinction between local and third party Cloud-Native services.**  To the CNF, both are attached resources, accessed via a URL or other locator/credentials stored in the [config](./config).  A [deploy](./codebase) of the X-factor CNF should be able to swap out a backing CNF with another CNF without any changes to the CNF's code.  A VPN should be swappable with another VPN. Likewise, a firewall CNF could be swapped with a third-party firewall service without code changes.  In both cases, only the resource handle in the config needs to change.

Each distinct backing Cloud-Native service is a *resource*.  For example, a CNF is a resource; a MySQL database is a resource; two MySQL databases (used for sharding at the application layer) qualify as two distinct resources.  The X-factor CNF treats these services or databases as *attached resources*, which indicates their loose coupling to the deploy they are attached to.

<img src="/images/attached-resources.png" class="full" alt="A production deploy attached to four backing services." />

Resources can be attached to and detached from deploys at will.  For example, if the CNF's database is misbehaving due to a hardware issue, the CNF's administrator might spin up a new database server restored from a recent backup.  The current production database could be detached, and the new database attached -- all without any code changes.
