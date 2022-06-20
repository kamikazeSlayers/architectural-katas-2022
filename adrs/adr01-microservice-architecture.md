# Microservices Architecture v/s Monolithic Architecture

## Status
Approved

## Context
The Spotlight App Project is an app that connects non profit organisations on a collaborative platform to make their offerings related to career building, discoverable to candidates of diverse under represented groups.
The users of the app include non-profits, candidates, admins, career mentors, community leaders.
The functionality provided by the platform is diverse and needs to cater to all the users requirements in addition to creating operational and analytical reports.

## Decision 
A microservices architecture would better suit the needs of this application

## Rationale
The application needs to be scalable to millions of users. The performance of the system determines engagement with the application by the users. 
The system should also be able to evolve based on the customer needs. The infrastructure needs to be maintainable and scalable.
For this reason, a microservices architecture best suits the requirements. Each service can be scaled individually based on requirements. New microservices can be easily added.
Each service can be developed and deployed independently enabling agile development frameworks, and minimal downtimes. 

## Consequences
Debugging and monitoring can be an issue in a microservices architecture. 
Using metrics collection, logs for every service and distributed tracing can help resolve this issue. 
