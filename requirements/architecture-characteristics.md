# Architecture Characteristics
In this document, we list the architecture characteristics that we considered important for the system.

## Availability

## Security

## Scalability

## Performance

## Feasibility (Cost)

## Deployability

## Simplicity

## Maintainability

## Mapping of Non Functional Requirements to Architecture Characteristics
The following table lists the NFRs that we considered and maps them to relevant architecture characteristics:
| S. No. | Description | Architecture Characteristic |
|:---:|---|:---:|
| 1 | The user should be able to navigate the system with ease with prompts where necessary and a complete user guide to be able to use the app without any training or assistance | Usability |
| 2 | Assume initial of 1,000,000 users ( NPOs and candidates), 10% users online at any given point in time - 100000 user active - 10000 users online * 10 rpm Thus, platform must support 100K rpm. | Scalability |
| 3 | Assume 1 offering/service includes files and downloadables worth 100MB. If 1 NGO supports upto 10 offerings, each NGO would need 1GB data. For initial 100 NGOs, we would need upto 100GB storage. If 10 NGOs are added per month, storage requirements increase by 10GB per month. In order to support upto 1000 NGOs over a period of 10 years, we need to be able to support upto 1TB storage. | Scalability |
| 4 | Candidate matching offerings must be made available within 10 seconds | Performance |
| 5 | New posts to community forums must be visible within 1 second | Performance |
| 6 | New profiles, profile page must be created within 5 seconds  | Performance |
| 7 | The platform must be available at all times except during maintenance activities. Target availability 99.9% of the time | Availability |
| 8 | The candidates and NPOs must only be able to view their own reports and metrics. Reports and metrics / data related to other candidates and NPOs must be restricted | Security |
| 9 | The system must be modular and support reusability of components and resources where possible | Maintainability |
| 10 | Regular upgrades to the infrastructure is performed to keep the dependencies and the system up to date with bug fixes, vulnerabilities, etc with minimal downtime | Maintainability |
| 11 | Resources, technologies, and infrastructure required to create the platform must be cost effective since it is used by non profit organisations | Cost Effectiveness |