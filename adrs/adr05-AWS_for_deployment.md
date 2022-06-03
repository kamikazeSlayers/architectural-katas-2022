# Use AWS as Cloud Provider

## Status
Proposed

## Context
Using a managed service powered by a public cloud provider vs managing everything on our own affects a lot of the architectural characeristics:
- Scalability (out-of-the-box)
- Maintainability
- Deployability

## Decision 
The Spotlight platform will use Amazon AWS as the cloud provider. 
*We chose AWS because of our past expertise in the same.*

## Rationale
- Easier maintanability and deployability of the overall system.
- On premise deployments require dedicated support and are hard to scale.
- With managed services, scalability comes out-of-the box.
- Because of microservice based architecture, many different types of infrastructural components need to be deployed. Gaining deployment expertise for all components compared to gaining expertise for a single cloud provider reduces the effort considerably.

## Consequences
- Engineers responsible for deployment (devops) need to be trained for AWS services.