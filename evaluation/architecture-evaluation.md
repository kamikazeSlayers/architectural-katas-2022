# Architecture Evaluation

## Non-functional Requirements and corresponding Architecture Characteristics

#### Restating the NFR to architecture characteristic mapping here for the purpose of architecture evaluation. 

| S. No. | Non functional Requirement | Architecture Characteristic |
|:---:|---|:---:|
| N1 | The user should be able to navigate the system with ease with prompts where necessary and a complete user guide to be able to use the app without any training or assistance | Usability |
| N2 | Searching for Non profits, offerings, candidates must be made possible including typos in the search fields | Usability |
| N3 | Assume total users in the system are around 1,000,000 (NPOs and candidates), active users are 10% of the total users and concurrent users are 10% of the active users (as per [widely accepted rule of thumb](https://www.ibm.com/docs/en/cognos-analytics/10.2.2?topic=SSEP7J_10.2.2/com.ibm.swg.ba.cognos.crn_arch.10.2.2.doc/c_arch_estimatingconcurrentusers.html)). We get 100,000 active users with 10,000 users online. <br/> Considering 10 rpm for any user interacting with the system, the platform must support 100K rpm. | Scalability |
| N4 | Assume 1 offering/service includes files and downloadables worth 100MB. If 1 NGO supports upto 10 offerings, each NGO would need 1GB data. For initial 100 NGOs, we would need upto 100GB storage. If 10 NGOs are added per month, storage requirements increase by 10GB per month. In order to support upto 1000 NGOs over a period of 10 years, we need to be able to support upto 1TB storage. | Scalability |
| N5 | New entity updates must be discoverable / searchable within 10 seconds | Performance |
| N6 | Search results must be made available within 2 seconds | Performance |
| N7 | All front end pages must load within 5 seconds | Performance |
| N8 | The platform must be available at all times except during maintenance activities. Target availability 99.9% of the time | Availability |
| N9 | The candidates and NPOs must only be able to view their own reports and metrics. Reports and metrics / data related to other candidates and NPOs must be restricted | Security |
| N10 | The system must be modular and support reusability of components and resources where possible | Maintainability |
| N11 | Regular upgrades to the infrastructure is performed to keep the dependencies and the system up to date with bug fixes, vulnerabilities, etc with minimal downtime | Maintainability |
| N12 | Resources, technologies, and infrastructure required to create the platform must be cost effective since it is used by non-profit organisations | Cost Effectiveness |

#### Architectural Elements

| S. No. | Architectural Elements |
|:---:|:---:|
| A1 | [Microservices Architecture](../adrs/adr01-microservice-architecture.md)|
| A2 | [Event Driven Architecture](../adrs/adr02-eda-architecture.md)|
| A3 | [Search powered by ElasticSearch](../adrs/adr07-elastic-search_for_search.md)|
| A4 | [NoSQL Database for Storage](../adrs/adr03-sql-vs-nosql.md)|
| A5 | [Object store for pdfs, images](../architectural-views/platform-management-subsystem.md#object-store) |
| A6 | [Content Delivery Network](../architectural-views/platform-management-subsystem.md#content-delivery-network)|
| A7 | [Community Feed / Ranking Cache](../architectural-views/community-forum-management-subsystem.md#feed--ranking-cache-manager)|
| A8 | [Caching user and non profit information](../adrs/adr06-caching.md) |
| A9 | [AWS deployment in multiple availability zones](../architectural-views/physical-view-aws-deployment.md#multiple-availability-zones)|
| A10 | [API Gateway for Throttling Requests](../architectural-views/aws-api-gateway.md#throttling)|
| A11 | [Load balancing at API Gateway](../architectural-views/aws-api-gateway.md#load-balancing) |
| A12 | [Caching at API Gateway](../architectural-views/aws-api-gateway.md#caching)|
| A13 | [AWS for Deployment](../adrs/adr05-AWS_for_deployment.md)|
| A14 | [Role based authorisation](../architectural-views/platform-management-subsystem.md#user-management) |
| A15 | [Distributed tracing, monitoring and logging](../architectural-views/observability.md)|
| A16 | [Low cost alternatives](./cost-analysis.md#note-on-cost-savings)|

## Evaluation

| NFR | Architectural Elements<br> Fulfilling NFR | Notes | TradeOff (if any) | Risk (if any) | Recommended implementation <br> approach ( if applicable)
|:---:|---|---|---|---|:---:|
| N1 (Usability) | A1, A3 | Microservices architecture makes it flexible to add support for any additional services that can enhance usability. <br>Search tool enhances user experience and ease of finding resources/ non profits/ candidate information and so on. |  |  | Most of the usability aspects such as easy navigation, simple and intuitive UI, prompts for various actions, and so on must be taken care of when designing and implementing the front end of the application. |
| N2 (Usability) | A3 | | | | |
| N3 (Scalability) | A1, A2, A7, A8, A11, A12| | |While these architectural styles, caching help in scaling to get high throughputs, sufficient load testing and benchmarking, fixing bottlenecks in the implementation and so on must be done to get the desired scale|Setting up a load test environment to benchmark, test and measure would prove effective in building a scalable system|
| N4 (Scalability) | A4, A5 | | Using higher or lower capacity storages for cache, database may increase/decrease [cost accordingly](./cost-analysis.md#cost-analysis). | Appropriate storage instances must be allocated considering the volume of data to be stored else, there is risk of insufficient storage and consequent data loss |   |
| N5 (Performance) | A2, A3 | | | | |
| N6 (Performance) | A3, A6, A12 | Caching at API Gateway level would help faster retrieval of common search query results | | |Pagination can be implemented to retrieve the search results and front end should support the same|
| N7 (Performance) | A6, A7, A11, A12 | | | |Lazy loading of content, pagination implementation, on the front end and at the API level, could help improve the performance |
| N8 (Availability) | A9, A10, A15 | For Amazon EC2 with all running instances deployed in multiple AZs in the same region, AWS guarantees an [SLA of at least 99.99%](https://aws.amazon.com/compute/sla/). In addition, using [observability tools](../architectural-views/observability.md) to monitor the system metrics can help in early detection of high error rates, issues that can affect the Service Level Agreement ( SLA) of the service.|  |  |Appropriate throttling policies must be implemented at the API Gateway to protect from DDoS attack that can affect availability of the service|
| N9 (Security) | A14 |  |  |  | Individual services would need to implement authorisation using roles from the User management service and ownership verification to resources in their database |
| N10 (Maintainability) | A1, A2 |This comes out of the box for a system that uses microservices and event driven architectures. It allows for easily extending the system to include additional services, replace subsystems with out of the box solutions, and so on.| | | |
| N11 (Maintainability) | A1, A2, A13 | Microservices architecture and event driven architecture enable agility and loose coupling. As a result deployments, upgrades to one service does not bring down the entire service. Deployments of each microservice can take place independently, ensuring continuous integration and continuous delivery. AWS also supports minimal to no downtime in performing updates to the infrastructure and upgrading to different tiers.|   |Unexpected events during a maintenance activites may result in longer down times. So it would be good to keep customers/stakeholders informed about the possibility of such events|Major maintenance activities must be performed during times when there is least activity or/ less traffic|
| N12 (Cost Effectiveness) | A16 | Initial implementation can always start with basic tiers, and later can be upgraded to higher tiers based on usage. This would help save costs and reap the benefits of a distributed microservices architecture. |   |  Over provisioning of resources can lead to wastage nad increased costs|   |
