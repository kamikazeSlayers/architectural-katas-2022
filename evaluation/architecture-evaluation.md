# Architecture Evaluation

## Non-functional Requirements and corresponding Architecture Characteristics

Restating the NFR to architecture characteristic mapping here for the purpose of architecture evaluation. 

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
