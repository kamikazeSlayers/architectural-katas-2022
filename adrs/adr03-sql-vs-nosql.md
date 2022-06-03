# SQL vs NoSQL Database Considerations

## Status
Proposed

## Context
Choosing the type of database technology depends on the use-case you are building. Spotlight platform requires different database solutions to implement use-cases based on different needs. Some require high scale and thus horizontal scalability, some require flexible schema mappings whereas some require relational structure and referential integrity.

## Decision 
Spotlight platform shall use a mix of SQL and NoSQL databases.
SQL database shall be used wherever relational mappings/referential integrity is important.
NoSQL database shall be used where we large volume of data is expected and/or the schema is flexible.

## Rationale
- Overanalyzing SQL vs NoSQL and making the wrong choice can be catastrophic if you are building the product for next 10 years.
- Different use-cases require data-modelling approaches and there is no one-size-fits-all solution.
- Community forums require high scale based on the volume of post each actor in the system could be publishing. This leads future horizontal scalability requirements which are provided out-of-the-box by NoSQL databases.

## Consequences
- The application has to understand different database schemas and employ specific query languages.
- Engineers in the team also need to be familiar with both SQL based and NoSQL based databases.