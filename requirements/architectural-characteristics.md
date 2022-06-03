## Non Functional Requirements


<table>
  <tr>
   <td>
   </td>
   <td>Description
   </td>
   <td>Architectural Characteristic
   </td>
  </tr>
  <tr>
   <td>1
   </td>
   <td>The user should be able to navigate the system with ease with prompts where necessary and a complete user guide to be able to use the app without any training or assistance
   </td>
   <td>Usability
   </td>
  </tr>
  <tr>
   <td>2
   </td>
   <td>Assume initial of 1,000,000 users ( NPOs and candidates), 10% users online at any given point in time
<p>
100000 user active
<p>
10000 users online  * 10 rpm
<p>
Platform must support 100K rpm.
   </td>
   <td>Scalability
   </td>
  </tr>
  <tr>
   <td>3
   </td>
   <td>Assume 1 offering/service includes files and downloadables worth 100MB.

If 1 NGO supports upto 10 offerings, each NGO would need 1GB data.

For initial 100 NGOs, we would need upto 100GB storage.

If 10 NGOs are added per month, storage requirements increase by 10GB per month.

In order to support upto 1000 NGOs over a period of 10 years, we need to be able to support upto 1TB storage.
   </td>
   <td>Scalability
   </td>
  </tr>
  <tr>
   <td>4
   </td>
   <td>Candidate matching offerings must be made available within 10 seconds
   </td>
   <td>Performance
   </td>
  </tr>
  <tr>
   <td>5
   </td>
   <td>New posts to community forums must be visible within 1 second
   </td>
   <td>Performance
   </td>
  </tr>
  <tr>
   <td>6
   </td>
   <td>New profiles, profile page must be created within 5 seconds
   </td>
   <td>Performance
   </td>
  </tr>
  <tr>
   <td>7
   </td>
   <td>The platform must be available at all times except during maintenance activities. Target availability 99.9% of the time
   </td>
   <td>Availability
   </td>
  </tr>
  <tr>
   <td>8
   </td>
   <td>The candidates and NPOs must only be able to view their own reports and metrics. Reports and metrics / data related to other candidates and NPOs must be restricted
   </td>
   <td>Security
   </td>
  </tr>
  <tr>
   <td>9
   </td>
   <td>The system must be modular and support reusability of components and resources where possible
   </td>
   <td>Maintainability
   </td>
  </tr>
  <tr>
   <td>10
   </td>
   <td>Regular upgrades to the infrastructure is performed to keep the dependencies and the system up to date with bug fixes, vulnerabilities, etc with minimal downtime
   </td>
   <td>Maintainability
   </td>
  </tr>
  <tr>
   <td>11
   </td>
   <td>Resources, technologies, and infrastructure required to create the platform must be cost effective since it is used by non profit organisations
   </td>
   <td>Cost Effectiveness
   </td>
  </tr>
</table>


