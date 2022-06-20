# Event Driven Architecture

## Status
Approved

## Context
We want to build a scalable and performant system capable of serving one million users, with a throughput of about 200K requests per minute. 

## Decision 
Use event driven architecture

## Rationale
Event-driven architectures are ideal for improving agility. 
They're commonly found in modern applications that use microservices, or any application that has decoupled components.
Event driven architectures scale easily to provide highly responsive systems. 
It enables asynchronous functionality that allows jobs to be processed as and when resources are available. 
It allows for loose coupling that enables building maintainable and fault tolerant systems. 

## Consequences
Data duplication and out of order events need to be handled carefully. 
It results in eventual consistency, which may or may not be desired based on the use cases. 
