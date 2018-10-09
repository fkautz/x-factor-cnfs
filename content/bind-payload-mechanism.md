---
title: "XVI. Bind by payload and mechanism"
date: 2018-10-09T15:10:51-07:00
draft: true
---

### Bind to other CNFs by payload and mechanism rather than by upstream or downstream CNF type

X-factor CNFs should be loosely coupled with other CNFs by binding only by a payload and mechanism tuple. By keeping the CNF loosely coupled, it can be arbitrarily chained as long as the data plane supports the mechanism and directly chained CNF supports the payload type.

The CNF is not responsible for determining where in the chain it should go or where it physically runs. That responsibility lies with the orchestrator. Likewise, the X-factor CNF should make no assumptions about its locality to another CNF. Instead, it should rely on the operator and orchestrator to correctly organize the chain.

Adhering to this principle gives the operator flexibility to reorganize CNFs in a chain based on technical and business requirements.
