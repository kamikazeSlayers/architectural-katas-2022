# Community Forum Management Subsystem
Community Forums are the heart of the Spotlight ecosystem that bring together all the involved users.  

See platform requirement [#1](../requirements/functional-requirements.md#functional-requirements) and non-profit requirement [#NP4](../requirements/functional-requirements.md#user-stories), candidate requirements [#C4, #C5](../requirements/functional-requirements.md#candidate), community leader requirement [#CL5](../requirements/functional-requirements.md#community-leader), career mentor requirement [#CM5](../requirements/functional-requirements.md#career-mentor) and admin requirements [#A1, #A2](../requirements/functional-requirements.md#admin).

<img src="../resources/images/community-forum-management.png" height="600"></img>
_Created using Lucidchart. Refer [here](https://lucid.app/documents/view/6ac4f17a-30bf-464b-91bb-589963999fcf)._

## Element Catalog 

#### Commmunity Forum Management Service

- Community Forum Management Service (CFMS) manages communities, community-memberships, forums, posts, post-votes, and user-rewards. It uses a SQL database to manage these entities and their relationships.

- CFMS and related services use event-driven architecture to support high scale and resiliency. It enables asynchronous processing of workflows and supports keeps the services uncoupled for flexibility and ease of development.

- CFMS publishes common interaction events (post CRUD, upvotes, user memberships to community etc.) into the Message Queue. 

- These events are consumed by "Feed / Ranking Cache Manager" to populate user-feeds into the Cache for faster retrieval.

- These events are also consumed by Search Service for faster discovery and retrieval of communities, posts etc. 

#### Post Service
- Post Service is responsible for create/read/update/delete operations on user posts and upload of assets to Object Store. It use a NoSQL key-value database that offers a scalable store for Posts. 

#### Feed / Ranking Cache Manager
- Feed / Ranking Cache Manager is responsible for intelligently computing the top-posts (based on upvotes, downvotes, views etc), managing the top ranking of posts in a feed (per community, per region etc.) and offers a way to retrieve most meaningful top posts per user.
- Redis Cache offers sorted data-structures that can help maintain entity ids in a ranked/sorted fashion. 

#### Search Service
- Search Service makes the common entities in a community (candidates, non profits, services, communities, posts etc.) searchable. It intelligently tags these entities for seamless discovery and retrieval.
- Search Service uses ElasticSearch for maintaining the search index.

## Out-of-the-box (OOTB) Offerings Considerations
In order to speed up the development process and save on costs in the initial phases, we evaluated some OOTB community platforms that fulfill Spotlight's community forum requirements. In order to keep the user engaged, we can build abstractions on top of these platforms giving us the following advantages:
- Avoid vendor lock-in: One offering can be replaced with another, given it provides programmatic access (APIs).
- Flexibile design: Third-party offering can be replaced with our own subsystem (desribed [above](#community-forum-management-subsystem)) based on  usage, scale and other required features.

### PeerBoard
There are many community platforms out there ([bbPress (Wordpress)](https://wordpress.org/plugins/bbpress/)/[Discourse](https://www.discourse.org/)), but [PeerBoard](https://peerboard.com) stands out because of the following reasons:
- Complete white label platform: Allows you to fully customize your community to fit your brand image
- Visibility and access controls: Global and group-level controls for content visibility and access rights.
- Email Notifications: Allow members to receive periodic updates with forum highlights, recent posts, or other high level forum details, at a glance.
- Free [Pricing](https://peerboard.com/pricing) Tier: Has a free option and 30-day trial period for the paid plans (starts at $29/month)
- Programmatic Access: You can use the API functionality to integrate with any platform.
- Numerous [integrations](https://peerboard.com/integrations) that give the ability to add all kinds of additional features to your community. 

The profession plan fulfills all platform requirements and is priced at only $79/month, very cheap compared to other solutions. If the team wants to save on costs and development effort, this could be great starting point.

## Related ADRs 
- [Microservices Architecture](../adrs/adr01-microservice-architecture.md)
- [Event Driven Architecture](../adrs/adr02-eda-architecture.md)
- [SQL v/s NoSQL](../adrs/adr03-sql-vs-nosql.md)
- [Caching using Cache Manager](../adrs/adr06-caching.md)
- [ElasticSearch as the Search Provider](../adrs/adr07-elastic-search_for_search.md)

## References
- [Comparison of Community Platforms | 2022](https://sellcoursesonline.com/best-online-community-platforms)
