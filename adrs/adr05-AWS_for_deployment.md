# Use AWS as Cloud Provider

## Status
Approved

## Context
Using a managed service powered by a public cloud provider vs managing everything on our own affects a lot of the architectural characeristics:
- Scalability (out-of-the-box)
- Maintainability
- Deployability

## Decision 
The Spotlight platform will use [Amazon AWS](https://aws.amazon.com/?nc2=h_lg) as the cloud provider. 

## Rationale
- Easier maintanability and deployability of the overall system.
- On premise deployments require dedicated support and are hard to scale.
- With managed services, scalability comes out-of-the box.
- Because of microservice based architecture, many different types of infrastructural components need to be deployed. Gaining deployment expertise for all components compared to gaining expertise for a single cloud provider reduces the effort considerably.

## Alternatives considered
- Other cloud providers like [Microsoft Azure](https://azure.microsoft.com/en-in/) and [Google Cloud Platform](https://cloud.google.com/) were evaluated. However, none of them match the maturity and feature capabilities of AWS.
  - For example, Redis based cache is highly utilized in the Spotlight App architecture. As per [Azure docs](https://docs.microsoft.com/en-us/azure/azure-cache-for-redis/cache-how-to-zone-redundancy), Zone redundancy support only works with non-clustered and non-geo-replicated caches currently. In addition, it doesn’t support private link, scaling, data persistence, or import/export. On the contrary, AWS [supports zone redundancy](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/AutoFailover.html) in cluster mode with geo-replication.
- In terms of costs too, we found that AWS offerings are cheaper that Azure and Google Cloud Platform. See the price comparison for managed Redis cache [here](https://blog.skeddly.com/2020/01/comparing-managed-redis-services-on-aws-azure-and-gcp.html).

## Consequences
- Engineers responsible for deployment (devops) need to be trained for AWS services.
