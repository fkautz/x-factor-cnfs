# The X Factors

## -- Factors adapted from the 12-factor methodology --

## [I. Codebase](./codebase)
### One codebase tracked in revision control, many deploys

## [II. Dependencies](./dependencies)
### Explicitly declare and isolate dependencies

## [III. Config](./config)
### Store config in the environment

## [IV. Backing services](./backing-services)
### Treat backing cloud-native services as attached resources

## [V. Build, release, run](./build-release-run)
### Strictly separate build and run stages

## [VI. Processes](./processes)
### Execute the app as one or more stateless processes

## [VII. Port binding](./port-binding)
### Not recommended in X-factor CNFs. However, if necessary, export services via port binding

## [VIII. Concurrency](./concurrency)
### Scale out via the process model

## [IX. Disposability](./disposability)
### Maximize robustness with fast startup and graceful shutdown

## [X. Dev/prod parity](./dev-prod-parity)
### Keep development, staging, and production as similar as possible

## [XI. Logs](./logs)
### Treat logs as event streams

## [XII. Admin processes](./admin-processes)
### Run admin/management tasks as one-off processes

## -- Factors unique to X-CNFs --

## [XIII. Do not require kernel modifications or modules](./process-containers)
### Run in an unmodified OS environment, without kernel modifications or custom modules

## [XIV. Payloads](./payloads)
### Explicitly state payload types consumed and produced

## [XV. Interface mechanisms](./mechanisms)
### List mechanisms supported in order of preference

## [XVI. Bind by payload and mechanism](./bind-payload-mechanism)
### Bind to other CNFs by payload and mechanism rather than by upstream or downstream CNF type

## [XVII. Metrics](./metrics-as-event-streams)
### Treat metrics as event streams
