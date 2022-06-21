# Cost Analysis (ballpark only)

## Context
High initial infrastructure expenditures are one of the obstacles in launching a new project. This poses a typical "chicken and egg" dilemma to justify the timing and need of investment into new products and features. It is important to pay attention on the costs and keep them minimal, especially until the platform gains traction. 

This document attempts to estimate a rough high-level ballpark short-term deployment cost of the overall architecture. While the costs presented in this document might not be accurate, these numbers can help in producing the final implementation plan (prioritizing features, estimating the return on investment for each architectural subsystem, using third-party offerings instead of building one, preparing short-term vs long-term strategy etc).  
 
Note that as more and more users sign-up and the platform gains traction, "the effective per unit cost" of the infrastructure is expected to reduce significantly. This is because [Economies of Scale](https://www.investopedia.com/terms/e/economiesofscale.asp) is highly prevalent on such backend systems.

## High-level Estimates (ballpark only)

This section provides high-level rougth ballpark estimates of the architecture. Please take these numbers with a pinch of salt as coming up with highly accurate estimates require building POCs, load-testing micro-services and in-depth experimentation.

### Assumptions
- To ensure high-availability, a minimum of two containers are assumed to be running in all micro-services. 
- The implementation team should use these cost estimates for rough high level ballparks only. The instance sizes assumed in this cost exercise must be re-evaluated keeping the expected traffic and performance of the implemented business logic in mind.
- Operational costs due to data I/O is not computed. In the initial phases, this cost is expected to be low due to low system usage.
- Costs are computed for US region.

### Cost Analysis 

<table>
  <tr>
   <td><b>Subsystem</b>
   </td>
   <td><b>Ballpark estimate</b>
   </td>
   <td><b>Monthly Cost ($)</b>
   </td>
  </tr>
  <tr>
   <td>User Management subsystem
   </td>
   <td>EC2 (t3.large) * 2 = $0.08*30*24 * 2 = $120 per month
<p>
MySQL = $200 per month
<p>
Azure Active directory - Free tier includes 500k directory objects = $600 per month (730 hours * $0.4 per hour)
   </td>
   <td>$320
   </td>
  </tr>
  <tr>
   <td>Platform Management subsystem
   </td>
   <td>Platform Management Service EC2 (t3.large) * 2 = $0.08*30*24 * 2 = $120 per month
<p>
MySQL = $80 per month
<p>
Db CDC Consumer (t3.large) * 2 = $120 per month
<p>
NP Offering manager (t3.large) * 2 = $120 per month
<p>
NP NoSQL Db (25 gb data in free tier) = $0 per month
   </td>
   <td>$440
   </td>
  </tr>
  <tr>
   <td>Search subsystem
   </td>
   <td>EC2 (t3.large) * 2 = $0.08*30*24 * 2 = $120 per month
<p>
Elasticsearch = $30 per month
<p>
Enrichment service EC2 (t3.large) * 2 = $0.08*30*24 * 2 = $120 per month
   </td>
   <td>$270
   </td>
  </tr>
  <tr>
   <td>Notification subsystem
   </td>
   <td>Notification service EC2 (t3.large) * 2 = $0.08*30*24 * 2 = $120 per month
<p>

Email Service / Push notification service EC2 (t3.large) * 2 = $0.08*30*24 * 2 = $120 per month
<p>
Meeting scheduler (outsourced with free tier)
   </td>
   <td>$240
   </td>
  </tr>
  <tr>
   <td>Community Forum subsystem
   </td>
   <td>Community forum management service EC2 (t3.large) * 2 = $0.08*30*24 * 2 = $120 per month
<p>

Post Service EC2 (t3.large) * 2 = $0.08*30*24 * 2 = $120 per month
<p>
NP NoSQL Db (assuming 100GB data) $0.25 per GB month * 75 GB with 25 GB in free tier = $30 per month
<p>
Feed / Ranking cache manager EC2 (t3.large) * 2 = $0.08*30*24 * 2 = $120 per month
   </td>
   <td>$390
   </td>
  </tr>
  <tr>
   <td>Analytics subsystem
   </td>
   <td>Assuming AWS Redshift basic tier as initial data is very low 
   </td>
   <td>$50
   </td>
  </tr>
  <tr>
   <td>Other common infrastructure components
   </td>
   <td>VPC = $90 per month
<p>
Load Balancing = 90 per month
<p>
Route 53 = $180 per month
<p>
Cache (cache.m5.large) * 2 = $80*2 per month
<p>
Message Bus (assuming 10 million messages) = $0.40 * 10 = $4
<p>
Object Store (assuming 10 million requests) = $0.005 * 10,000 = $50
   </td>
   <td>$550
   </td>
  </tr>
  <tr>
   <td><b>Total costs with on-demand infrastructure provisioning</b>
   </td>
   <td>
   </td>
   <td><b>$2250</b>
   </td>
  </tr>
  <tr>
   <td><b>Conservative savings with Reserved Instances</b>
   </td>
   <td>
   </td>
   <td><b>-$675 (assuming 30%)</b>
   </td>
  </tr>
  <tr>
   <td><b>Total cost with reserved instances (ballpark)</b>
   </td>
   <td>
   </td>
   <td><b>$1575</b>
   </td>
  </tr>
</table>


### Note on cost savings
- Costs can significantly be reduced (30-70%) by opting to reserve the instances on AWS. It is encouraged to make use of reserved instances wherever possible. 
- EC2 instance size of all micro-services is assumed to be t3.large. For initial bootstrapping, a smaller instance size can be used. Similarly, smaller instance sizes for Elasticache, RDS and other resources can be provisioned initially. AWS allows scaling up all these resources without downtime or with minimal downtime in some cases.
- Implementation plan should be derived keeping these costs in mind. For example, it might be prudent to use a third-party offering for Notification subsystem (Google Calendar) and Community Forum (Wordpress). At a later stage, these subsystems can be built in-house based on the usage, scale and required features. Start small, use ready-to-use third-party offerings for quick bootstrapping, iterate fast, and evolve.
- AWS offerings include Free Tier plans for almost all its offerings. That should bring the day-zero costs down while building/bootstrapping the system. These free tiers are not fully considered in the above estimates. 


## References
- [AWS EC2 pricing calculator](https://docs.aws.amazon.com/whitepapers/latest/how-aws-pricing-works/amazon-ec2-cost-breakdown.html)
- [Azure Active Directory pricing calculator](https://azure.microsoft.com/en-in/pricing/calculator/?&ef_id=CjwKCAjwtcCVBhA0EiwAT1fY70WE_XarbWVfsrJjXCkYgCwdEMmJIf9S1H1_xo2NUFuucTL5w84sBBoCyNoQAvD_BwE:G:s&OCID=AID2200195_SEM_CjwKCAjwtcCVBhA0EiwAT1fY70WE_XarbWVfsrJjXCkYgCwdEMmJIf9S1H1_xo2NUFuucTL5w84sBBoCyNoQAvD_BwE:G:s&gclid=CjwKCAjwtcCVBhA0EiwAT1fY70WE_XarbWVfsrJjXCkYgCwdEMmJIf9S1H1_xo2NUFuucTL5w84sBBoCyNoQAvD_BwE)
- [Price comparison of Elasticsearch and Algolia Search](https://www.prefixbox.com/blog/algolia-vs-elasticsearch/)
- [AWS Redshift pricing](https://aws.amazon.com/redshift/pricing/)
- [AWS SQS Pricing](https://aws.amazon.com/sqs/pricing/)
- [AWS Elasticache pricing](https://aws.amazon.com/elasticache/pricing)
- [AWS EC2 Reserved Instances](https://aws.amazon.com/ec2/pricing/reserved-instances/)
- [AWS Reserved Instances overview](https://aws.amazon.com/aws-cost-management/aws-cost-optimization/reserved-instances/)
- [AWS Elasticache Reserved Instances](https://aws.amazon.com/elasticache/reserved-cache-nodes/)
