# Event Driven Architecture

## Status
Approved

## Context
We want to build a scalable and performant system capable of serving one million users, with a throughput of about 200K requests per minute.
The app should be modular and maintainable allowing room for future extensibility and expansion. 

## Decision 
Use event driven architecture

## Rationale
We compared monolithic architectures to distributed architectures in [ADR01](./adr01-microservice-architecture.md).
We concluded that for our use case, a hybrid architecture combining microservices and event driven architecture would best suit our requirements.

Event-driven architectures are ideal for improving agility. 
They're commonly found in modern applications that use microservices, or any application that has decoupled components.
Event driven architectures scale easily to provide highly responsive systems. 
It enables asynchronous functionality that allows jobs to be processed as and when resources are available. 
It allows for loose coupling that enables building maintainable and fault tolerant systems. 

This loose coupling allows for easy plug and play with alternatives using third party solutions, 
or extending the existing architecture easily to support additional features.

For example, we have discussed using alternative Out of the box solutions for [meeting scheduler](../architectural-views/notification-and-meeting-scheduler-subsystem.md#out-of-the-box-ootb-offerings-considerations) to get started and for a quick time-to-market solution.
This can later be easily replaced by an enhanced in-house solution as discussed in the same view, without affecting the rest of the system.

This is the power of an event driven architecture making it scalable, modular and extensible.

## Consequences
Data duplication and out of order events need to be handled carefully. 
It results in eventual consistency, which may or may not be desired based on the use cases. 
