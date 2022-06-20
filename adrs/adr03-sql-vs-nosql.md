# SQL vs NoSQL Database Considerations

## Status
Proposed

## Context
Choosing the type of database technology depends on the use-case you are building. 
Spotlight platform requires different database solutions to implement use-cases based on different needs. 
Some require high scale and thus horizontal scalability, some require flexible schema mappings whereas some require relational structure and referential integrity.

## Decision 
Spotlight platform shall use a mix of SQL and NoSQL databases.
SQL database shall be used wherever relational mappings/referential integrity is important.
NoSQL database shall be used where large volume of data is expected and/or the schema is flexible.

## Rationale
Platform management service handles data related to the non-profits, community leaders, candidate needs, non-profit offerings, career mentors, and candidate career map.
We are handling diverse data from simple forms for career needs assessments, to links, resources, and so on for non-profit offerings.

Non-profit offerings can have a flexible schema. Some offerings may have reading materials, downloadable, links to videos, while some others may be more of location based services, etc.
Some non-profits may redirect candidates to their websites, while others may define offerings in terms of milestones that involves watching video links, reading content, and so on.
The schema for an NPO offering may evolve over time depending on the type of services. 

In case of maintaining information related to the Non profits, candidates, needs assessment, career road map, the data that is required to be stored ( table definition ) is not expected to change very often.

In all cases, we would be storing large objects in an object store such as S3 Bucket and only references to such objects would be stored in the database.

Keeping this in mind, we considered the following alternatives

#### Options considered:
- Using RDBMS to handle all kinds of data: Using RDBMS seemed to be a good option for all cases, since it allows for relational mappings between various entities, for example between candidates to career road maps, career road maps to non profit offerings, non-profits to non-profit offerings and so on. 
However, considering that non-profit offerings can have a flexible schema, we may have a sparse matrix for the non profit offering where some columns would apply to only certain offerings while other columns would have NULL values. We would need to keep adding columns for offerings which do the fit the existing schema. 
SQL does not scale out horizontally easily.  

- Using NoSQL for all scenarios: This would take care of the flexible schema required for the non profit offerings. 
All data pertaining to a non profit and its offerings would be stored as a single document. 
However, Relational mappings between the various entities would have to be handled by the application. 
Complex joins between data need to handled at the application level, which would otherwise be available out of the box in SQL databases.

- Using a mix of SQL and NoSQL
While SQL can be used in cases where the schema is fixed, and does not change often, does not involve large objects, etc, NoSQL database will be used for storing data with flexible schema. 
For example, while data related to all the non-profits can be maintained in the SQL database, the non-profit offerings will be maintained using the NoSQL database. 
This will allow us to continue to use the relational mappings between the different entities such as the NPOs, candidates, and so on.
While the non-profit offerings are stored in the NoSQL database, the id to the document in NoSQL database would be maintianed in the SQL database. This referential integrity between the SQL and NoSQL databse would need to be maintained by the application. 
However, the overhead is far less as compared to using only a NoSQL database.

  The same applies to community forums. While all user information is stored in SQL, posts, and all related entities are stored in NoSQL database for scale and performance.

#### Why mix of SQL and NoSQL is a better choice
- Over-analyzing SQL vs NoSQL and making the wrong choice can be catastrophic if you are building the product for next 10 years.
- Different use-cases require data-modelling approaches and there is no one-size-fits-all solution.
- Community forums require high scale based on the volume of post each actor in the system could be publishing. 
This leads future horizontal scalability requirements which are provided out-of-the-box by NoSQL databases.

## Consequences
- The application has to understand different database schemas and employ specific query languages.
- Engineers in the team also need to be familiar with both SQL based and NoSQL based databases.
- Referential integrity between the SQL and NoSQL databases need to be handled by the application.
