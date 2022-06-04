# Operational Reports

## Element Catalog 

#### API Endpoint

- The platform management service exposes endpoints to retrieve operational reports from the database such as: <br />
Number of candidates registered for an offering <br />
Number of completed career road maps <br />
Number of offerings provided by an NPO <br />
Region specific details on candidates and offerings <br />
and so on.

#### New Relic
New Relic can be easily integrated with AWS EC2 instances to fetch reports related to CPU and memory usage, thread profiling, etc. 

#### Integration with Prometheus and Grafana
The services can be configured to push metrics to services like Prometheus. A prometheus instance can be configured to run in the kubernetes cluster that pushes metrics to Grafana. You can then build visualisations on Grafana using queries on the data. It can help provide valuable operational insights such as traffic patterns, and can also help in the process of debugging. 
More details can be obtained: https://grafana.com/docs/grafana/v7.5/

