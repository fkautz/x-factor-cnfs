## [XIV. Payloads](./payloads)
### Explicitly state payload types produced and consumed

X-factor CNFs explicity state what type of payloads they produce and consume. Each X-factor CNF consumes one payload type and produces one payload type.

CNFs consume payloads with a given type. X-factor CNFs define the payload types they produce and consume in their CNF metadata. These payloads are network protocols which the CNF is programmed to interact with. Common payloads include IP, Ethernet and MPLS. More esoteric payloads may include tunnelling protocols such as VXLAN or CPE protocols such as Docsys.

Often, CNFs are chained together to produce a Service Function Chain (SFC). When a CNF describes what payloads it is capable of working with, the orchestrator can type check the chain's definition to ensure the chain is valid at both installation and upgrade time. If there are multiple CNFs providing the same function for different payload types, the correct CNF may also be selected at runtime.

Finally, the payload is defined separately from the interface mechanism. The CNF may be capable of handling multiple interface mechanisms for the same payload.
