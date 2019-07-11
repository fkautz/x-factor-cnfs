---
title: "XIII. Do not require privileges"
date: 2018-10-09T15:10:51-07:00
draft: true
---
### The CNF should run without privileges. Privileged actions should be managed by the scheduler and environment.

To achieve process isolation, X-factor CNFs are designed to run in process containers without privileges. Privileged actions may be requested by the container and performed by privileged delegate. Running unprivileged promotes loose coupling between environments, reduces the overall attack surface, and gives the scheduler the ability to clean up after the pod in the case of the pod failing.

The X-factor CNF methodology recognizes the need for hardware which requires additional kernel modules. When possible, kernel modules must follow standard Linux kernel device driver standards (TODO find link) and do not affect the kernel's runtime environment beyond enabling the device. These devices must also not be bound directly from the CNF. Instead, they are listed as an interface mechanism and injected into the container runtime by the orchestrator. The existence of a hardware device should not affect other CNFs.

# TODO
Some kernel modifications may be acceptable, e.g. DPDK or drivers. This should be immutable infrastructure with a clean interface for pods. In short, pods should not be allowed to modify their infrastructure.
