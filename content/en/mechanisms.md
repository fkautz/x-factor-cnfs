## XV. Interface mechanisms
### List mechanisms supported in order of preference

A given X-factor CNF lists in order of preference what types of interface mechanisms are supported for both its terminating and initiating interfaces. 

An interface mechanism is any serial/block device,, file or socket that is used to transport data in and out of the container. The most common type of interface mechanism is the Linux interface. Other common mechanisms include SR-IOV, vhost-user, shmem, unix sockets, or serial/block devices.

An X-factor CNF may list multiple preferences of what types of interface mechanisms it supports. However, only one mechanism will be wired in for the connection it terminates and only one will be wired in for the connection it initiates.

By listing these mechanisms explicitly, the orchestrator can coordinate with both the CNF and data plane to determine what the most fitting interface for the CNF should be. Likewise, the operator may choose to disable certain types of minterface mechanisms administratively for a given CNF to preserve resources for other CNFs which are in higher need when resources are scare, such as hardware devices.
