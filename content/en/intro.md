Introduction
============

Cloud-Native Network Function (CNF) developers may learn much by studying how 12 Factor Apps are built.  With X-Factor CNFs (X-CNF), we build on the lessons learned from building 12 Factor Apps.

Following these patterns will help guide you construct CNFs which are easier to develop, operate and maintain.

Like 12 Factor Apps, X-CNFs have the following properties:

* Use **declarative** formats for setup automation, to minimize time and cost for new developers joining the project;
* Have a **clean contract** with the underlying operating system, offering **maximum portability** between execution environments;
* Are suitable for **deployment** on modern **cloud** and **service provider** platforms, obviating the need for servers, virtual machines and systems administration;
* **Minimize divergence** between development and production, enabling **continuous deployment** for maximum agility;
* And can **scale up** without significant changes to tooling, architecture, or development practices.

X-CNFs also have additional properties not common in 12 Factor Apps which enable their use as a CNF:

* State their **payload type** for easy service function chaining orchestration;
* List their **supported mechanisms** supported mechanisms in order of preference to facilitate wiring to a data plane;
* Connect to **Cloud-Native Microservices** over their default **orchestration-managed** network interface;

The X-factor methodology can be applied to CNFs written in any programming language, and which use any combination of backing **network services** (bridge domain, subnet, VPN, ToR port, etc) communicating over a well defined **payload** (ethernet, IP, MPLS, VXLAN, etc) and **mechanism** (Linux interface, SR-IOV, memif, etc) to a **data plane** (physical, OVS, VPP). The X-factor CNF may also use any number of **Cloud-Native** services (database, queue, memory cache, etc).

## CNF Levels

Finally, a CNF level system is proposed. These serve two purposes:

1. Guide the community towards best practices that allow the CNF to fully leverage the Cloud-Native environment in which they live.
2. Describe the level of operational risk the service provider will take on when introducing a CNF into their environment.
