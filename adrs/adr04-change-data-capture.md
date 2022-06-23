# Change Data Capture (CDC)

## Status
Approved

## Context
Spotlight platform requires ease-of-use and engagement as hard requirements. For that, search becomes a critical piece to enhance discovery and retrieval of entities in the system that enhance the overall candidate experience and keep him engaged.
For search to work it has to stay up-to-date with any changes in the data set in a consistent manner. This gives rise to the problem of constantly keeping track of database changes in a scalable and resilient manner.

Change Data Capture (CDC) in databases is a set of software design patterns used to determine and track the data that has changed so that action can be taken using the changed data. This allows seamless tracking of database changes without polling the database or pushing updates as part of a distributed transaction to a separate channel like queue.

## Decision 
Spotlight platform will use the CDC pattern wherever applicable to track database changes.

## Rationale
- Tracking database changes at scale can overwhelm the database and hence degrade the user experience.
- Also with entities spanning across multiple services, keeping things consistent becomes hard.
- With CDC, all the updates can be tracked without additional overheads on the database or the application, and allow a single source (message queue) of truth from where the updates can be processed.

## Alternatives Considered
Another approach that was evaluated was where the service is responsible for publishing updates to a message broker whenever any changes in the database are committed. However, this suffered from the following drawbacks:
- Could lead to data inconsistencies because of the distributed nature of transaction, spanning across the database and the message broker.
- It's often undesirable to couple the service to both the database and the message broker.

## Consequences
- Requires special infrastructural components to understand CDC streams and process them accordingly

## References
- [Change Data Capture](https://en.wikipedia.org/wiki/Change_data_capture)
- [An Introduction to Change Streams | MongoDB Blog](https://www.mongodb.com/blog/post/an-introduction-to-change-streams)