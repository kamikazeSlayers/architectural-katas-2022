# ElasticSearch as the Search Provider

## Status
Accepted

## Context
Search is a critical piece of the Spotlight platform that  enables discovery and retrieval of all entities in the system,  enhancing the overall candidate experience and engagement.

The following requirements were identified keeping the above goals in mind:
- Must support fuzzy logic i.e. provider accurate results in spite of typos in the query string in the search.
- Must be scalable for huge amounts of data (in order to support search based on community posts as well).
- Should have a relatively low response time.

While analyzing the above, the following search engines were considered that were best suited for these requirement:
1. ElasticSearch
2. Algolia
3. MongoDB based Search

For more details on the comparison done, see the [Alternatives Considered](#alternatives-considered) section.

## Decision 
Spotlight Platform will use ElasticSearch as the search provider.

## Rationale
ElasticSearch has several advantages when compared to its [alternatives](#alternatives-considered):
- Provides better scalability.
- Cost effective. Other solutions become costlier once the records increase in number.
- Flexible data model which is unparalleled compared to others. One can nest fields as deeply as required, and have as many fields as needed. There is no need to declare a schema beforehand.
- Simple query structure that provides an easy way to write and fetch data for complex queries.

## Alternatives Considered

### Algolia

While [Algolia](https://www.algolia.com/) is fast and easy to implement and has better integrated handling of typos, we decided to reject it because of the following reasons:
- Algolia is an expensive solution
- Scaling can be difficult with Algolia

### MongoDB Based Search vs ElasticSearch

Even though [MongoDB](https://www.mongodb.com/docs/manual/text-search/) is faster in case of updating/indexing the data, we decided to reject it because of the following reasons:
- Full text search capabilities are only available as part of MongoDB Atlas which is a premium solution.
- Recommendation engine is not available in MongoDB at all.
- ElasticSearch provides much superior text-based search features.

## Consequences
- ElasticSearch has a steep learning curve.
- Updates are slower in ElasticSearch as it needs to re-index the whole **document**.
- ElasticSearch is cost-effective, but the costs are fixed and not proportional to the number of search requests. This can be a disadvantage in the initial phases when the number of users are low.