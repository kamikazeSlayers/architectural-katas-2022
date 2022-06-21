**<span style="text-decoration:underline;">Spotlight App 1.0</span>**

## Our Mission

Diversity Cyber Council is a 501c3 Non-Profit that serves under-represented demographics in the tech industry by facilitating education, training, and staffing opportunities to establish a sustainable and diverse talent pipeline to the workforce.

## Vision

Our vision is to enhance inclusion and representation in the tech industry through training, mentoring, networking, and visibility programs.

## Goal

Our goal is to establish a sustainable and diverse talent pipeline that extends career equity to underrepresented demographics by providing access to competent training programs that lead to direct employment opportunities. 

## Users

1. Non profit organizations
2. Candidates
3. Community leaders
4. Career mentors
5. Admins

## Functional Requirements

1. The Platform must establish a way to incentivize engagement such as sharing of resources, collaboration, networking, facilitating introductions, and partnerships
2. The Platform must categorize/tag nonprofit support services to match candidate needs identified in the onboarding assessment to include but not limited to
    * Resume Writing Services	
    * Interview Prep	
    * Free Business Attire
    * Apprenticeship Program Registration	
    * Training Program Registration 	
    * College & University Registration 
    * Free Grocery & Meal Services	
    * Discounted Rent & Housing Services	
    * Daycare/Child Care Services
    * Mentorship/Career Advocate Services		
3. End-Use Ease of Use is a hard requirement
4. Tracking candidate progress is a hard requirement
5. Tracking engagement is a hard requirement
6. The Platform must provide a way to allow Non-Profits to publicize offerings to the platform that can provide some level of automatic matching for Candidate requests.
7. The Platform allows offerings to contain rich text, links, and downloadable readable content such as PDFs, but no other downloads.
8. Each offering must support a certain list of properties (defined by the platform), such as name, organization description, website, unique identifier (assigned by the Administrators) and other identification information.
9. The Platform must provide both operational reports (number of candidate matches / period, number of offerings / region, and so on) and analytical reports (projections of future desirable career paths, Offering gaps in a region based on demand, and so on) for use by Administrators.
10. Accessibility (to cater to users belonging to all categories) 

### User Stories

#### Non Profit

|Id|User Story|Area|
|--- |--- |--- |
|NP1|As a non profit organisation, I want to onboard my non-profit to the Platform by providing my profile, list of offerings|Onboarding|
|NP2|As an NPO, I want to be able to upload various resources, useful links, outside of the offerings to my page.|Profile Management|
|NP3|As a non profit organisation I should be able to create/update/delete offerings, create shared offerings with other NPOs|Offering Management|
|NP4|As an NPO, I should be able to communicate with other NPOs. This can be through community meetings or community forums|Collaboration|
|NP5|As a non profit organisation I want to view my profile and list of candidates who have enrolled for all my offerings|Reporting|
|NP6|As an NPO, I want to be able to view engagement reports and other useful reports related to my offerings and engagement|Reporting|


#### Candidate

|Id|Description|Area|
|--- |--- |--- |
|C1|As a candidate i want to be able to create/update/delete my profile|Onboarding|
|C2|As a candidate i want to be able to complete needs assessment|Onboarding|
|C3|As a candidate I want to be able to browse all available offerings on the platform in addition to the matching offerings provided based on the needs assessment|Career Roadmap|
|C4|As a candidate, I want to engage with my community mentor in order to keep track of my progress, who can also help support by providing various other useful resources, links and mentorship.|Collaboration|
|C5|As a candidate, I want to be able to communicate with the NPOs via community forums, as questions related to offerings, get doubts cleared, and so on.|Collaboration|
|C6|As a candidate, I want to be able to create, update my career map based on my needs and interests and keep track of my progress.|Career Roadmap Tracking|
|C7|As a candidate, I want to visit community pages, participate in forums|Community|


#### Community Leader

|Id|Description|Area|
|--- |--- |--- |
|CL1|As a community leader, I want to be able to verify the NPO’s authenticity based on the information provided.|NPO onboarding|
|CL2|As a community leader, i want to be able to connect with NPOs via 1:1 meetings and community meetings, email and phone.|Collaboration|
|CL3|As a community leader, i want to be able to approve announcements and important posts in community forums to reduce spam and noise|Platform Management|
|CL4|As a community leader, I want to be able to create new communities based on services and offerings by various NPOs.|Community Management|
|CL5|As a community leader, based on my skills, i can be a leader for 1 or more communities with an upper limit of the number of communities that i can manage|Collaboration|
|CL6|As a community leader, I view operational reports, usage and engagement statistics of the communities I manage|Reporting|

#### Career Mentor

|Id|Description|Area|
|--- |--- |--- |
|CM1|As a career mentor, i need to be able to help prioritise the career map for my candidates|Candidate onboarding|
|CM2|As a career mentor, I need to be assigned candidates based on my expertise and skills with an upper limit on the number of candidates I can manage at any given point.|Collaboration|
|CM3|As a career mentor, I need to be able to keep track of my candidates progress, via meetings and viewing the career map.|Career Roadmap Reporting|
|CM4|As a career mentor, I need to be able to suggest offering and services to my candidates based on their needs|Career Roadmap Tracking|
|CM5|As a career mentor, I need to be able to communicate with NPOs via community forums and other communication medium, eg. email.|Collaboration|

#### Admin

|Id|Description|Area|
|--- |--- |--- |
|A1|As an admin, I want to be able to manage the community forum, avoid spam, bring down posts/offerings, disable NPOs/candidates that do not abide by the principles of the platform.|Platform Management|
|A2|As an admin I want to be able to categorise NPOs with unlisted services into the right community or create new communities.|NPO onboarding|
|A3|As an admin, I want to be able to approve NPOs to the platform after the authenticity is verified|NPO onboarding|
|A4|As an admin, I want to be able to view operational reports and analytics reports for the Spotlight App.|Reporting|

## Assumptions

1. Platform will need to ensure a minimum number of mentors and community leaders based on the number of candidates and NPOs.
2. There would be an upper cap on the number of people that a person can mentor.
3. Community is a separate entity always associated with a forum.
4. An NPO can be a part of multiple communities.
5. Community leaders are already part of the platform who are proficient in certain skill sets (services).
6. There will be a default community that an NPO is assigned to before it is assigned to a community that suits its services and offerings by a community leader
7. Platform will match the community leader to a NPO based on the services, location etc. 
8. If there is a new service, broadcast the community leader election request among "n" community leaders. If the request is not accepted, then we fall back to platform admin.
9. One user can have multiple roles (NP, Candidate ...)
10. Community leader must verify authenticity of NP and approve.
11. Meetings can be physical or virtual. In case of virtual meetings, the platform will rely on third-party services/applications like Google Meet, Zoom etc.
12. Posts in a community forum can contain text and one or more images upto 10 MB.

## Constraints

1. Cost is a contraint. The solution must be cost effective since it is for use by non profit organisations.
2. Candidates who avail the services do not pay for them
3. The platform should be supported on both mobile and desktop devices.
4. The platform should support any browser type like google chrome, mozilla firefox, IE, Safari, etc.
5. The UI should be simple and intuitive
6. NPO offerings only include rich text, links, downloadable reading content eg. PDF. No videos and music formats are supported. 
7. The app should be accessible to all diverse kinds of users. 
