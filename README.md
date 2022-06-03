# The Spotlight App Project - Illuminate Possibilities

<img src="images/spotlight.jpeg"></img>

## Introduction
Diversity Cyber Council is a 501c3 Non-Profit that serves under-represented demographics in the tech industry by facilitating education, training, and staffing opportunities to establish a sustainable and diverse talent pipeline to the workforce. Their vision is to enhance inclusion and representation in the tech industry through training, mentoring, networking, and visibility programs. Their goal is to establish a sustainable and diverse talent pipeline that extends career equity to under-represented demographics by providing access to competent training programs that lead to direct employment opportunities. 

### The Spotlight App Project
The Spotlight App Project is a sustained effort to amass a coalition of nonprofits in order to address specific needs within the communities, by leveraging a centralized platform as the base of operations to collaborate and make a collective impact. 

The project aims to solve two problems: 
1. The decentralization and lack of support between nonprofits create gaps of service and overall impact. 												
2. The lack of visibility of nonprofit groups and offerings creates a barrier of access to the people we aim to serve. 

This architecture document aims at providing a technology solution that serves the purpose of enhancing visibility, support, and collaboration of nonprofits serving similar needs in the community and operates as a candidate case management platform.

<img src="images/spotlight-community.jpg" height="400"></img>

## Requirements
Please go through the provided [requirement document](https://docs.google.com/document/d/1XjEpcGJ87xYg1eWN9eE0_tH7te5HcVAgPvoONLHY4qQ/edit) to understand the requirements better. These requirements were the main drivers for the design decisions in our architectural proposal.
- [Functional Requirements](./requirements/functional-requirements.md): Here you'll find the different actors in the system, functionalities each user can do (aka user stories), assumptions and constraints that we considered during the process.
- [Architecture Characteristics](./requirements/architecture-characteristics.md): The architecture design must incorporate these characteristics along with the above mentioned functional requirements.

## Architectural Evaluation
The following points outline how does the architecture support some of the hard-requirements of this platform:
### Ease of Use
To facilitate ease-of-use, the Spotlight App -
- Supports multiple user surfaces - Web and Mobile. This enables users to access the platform on-the-go as per their preference.
- Creates device-size specific renditions of images present in the assignments, profiles and community posts. Based on the user-device, appropriate image rendition is returned for a seamless experience.
- Ensures that all entities in the system (candidates, non profits, services, communities, posts etc.) are searchable. It intelligently tags for seamless discovery and retrieval.
- Uses UX ensures seamless onboarding experience, continuous progress tracking, constant feedback and access to community forums.

### Engagement
To facilitate engagement, the Spotlight App -
- Rewards the candidates and non-profits with points and badges
- Highlights the top non-profits, top candidates, top communities, top community posts in the app. These top entities are computed platform wide and globally over a period of time (weekly, monthly etc).
- Supports notifications on all possible user surfaces - Web and Mobile. This helps in keeping the users connected and engaged.
- Ensures that the community leader and career mentor play a critical role in the engagement.
- Provides community forums where candidates, non-profits and community leaders can collaborate, share announcements/posts and ask questions.

### Analytics / Reporting
To facilitate analytical reporting, the Spotlight App -
- Provides powerful visualisation tools to analyse data to gain meaningful insights.
- Supports SQL based dashboards to create reports and visualisations for custom queries.
- Is powered by machine learning to perform predictive analysis, data classification etc. to plan for future requirements, gaps in the services and so on.

## Architecture
The main part of the design proposal is the set of architecture views seen below:
- [Analytical Architecture](./architectural-views/analytical-architecture.md)
- [Community Forum Management Architecture](./architectural-views/community-forum-management.md)
- [Search and Enrichment Service Architecture](./architectural-views/search-and-enrichment-service.md)
- [Physical View Architecture (AWS Deployment)](./architectural-views/physical-view-aws-deployment.md)

## ADRs
Below are the key architectural decision records:
- Microservice vs Monolith Style of Architecture
- Database Considerations: MySQL vs NoSQL
- Event driven architecture (EDA)
- Change Data Capture (CDC)
- AWS for deployments
---

## Directory Structure
- [ADRs](./adrs/) - contains all architecture decisions.
- [Architectural Views](./architectural-views/) - contains detailed architectural views with supporting documentation for every component.
- [Images](./images) - contains architecture diagrams and other supporting images. 
- [Requirements](./requirements/) - contains the requirements and architecture characteristics considered.
