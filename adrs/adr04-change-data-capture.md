# Change data capture

## Status
Proposed

## Context
Spotlight platform requires ease-of-use and engagement as hard requirements. For that, search becomes a critical piece to enhance discovery and retrieval of entities in the system that enhance the overall candidate experience and keep him engaged.
For search to work it has to stay up-to-date with any changes in the data set in a consistent manner. This gives rise to the problem of constantly keeping track of database changes in a scalable manner.

Change data capture (CDC) in databases is a set of software design patterns used to determine and track the data that has changed so that action can be taken using the changed data. This allows seamless tracking of database changes without polling the database or pushing updates to a separate channel like queue.

## Decision 
Spotlight platform will use the CDC pattern wherever applicable to track database changes.

## Rationale
- Tracking database changes at scale can overwhelm the database and hence degrade the user experience
- Also with entities spanning across multiple service, keeping things consistent becomes hard
- With CDC, all the updates can be tracked without additional overheads on the database or the application, and allow a single source (message queue) from where the updates can be processed.

## Consequences
- Requires special infrastructural components to understand CDC streams and process them accordingly