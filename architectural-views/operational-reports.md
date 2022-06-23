# Operational Reports
The Spotlight architecture supports generation of periodic and on-demand operational reports such as number of candidate matches in a given period, number of offerings in a given region, and so on.

See platform requirement [#9](../requirements/functional-requirements.md#functional-requirements), non-profit requirement [#NP5](../requirements/functional-requirements.md#user-stories), candidate requirement [#C6](../requirements/functional-requirements.md#candidate), community leader requirement [#CL6](../requirements/functional-requirements.md#community-leader), career mentor requirement [#CM3](../requirements/functional-requirements.md#career-mentor) and admin requirement [#A4](../requirements/functional-requirements.md#admin).

## Element Catalog 

### Reporting Approaches

The platform management service exposes endpoints to retrieve operational reports such as:
- Number of candidates registered for an offering
- Number of completed career roadmaps
- Number of offerings provided by an NPO
- Region specific details on candidates and offerings
- and more

The platform management service fetches the data from its SQL database on-demand. To keep the critical functionality of the platform management service unimpacted by the reporting workflows, this service can fetch data from read-replicas of the database. 

If the reports computation exerts high pressure on the database, then platform management service can choose to periodically pre-compute the reporting data and store it back in the database. This pre-computed reporting data can then directly be returned when a user requests for the reporting data. It is preferrable to keep the reporting queries light and optimized and this approach should be treated as a fallback only. It is recommended to treat this fallback approach as an exception rather than the norm.
