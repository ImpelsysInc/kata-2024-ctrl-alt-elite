# ADR 18: Object Store for Storing Resume Data

## Date:
2024-09-30

## Status:
Accepted  

## Context:
The HR Orchestrator engine aims to manage resume as a key data component. Storing resume data efficiently and securely is crucial for facilitating quick access and searchability while ensuring compliance with data privacy regulations.

## Decision
We have decided to use an Object Store for storing resume data within the HR Orchestrator engine. This choice supports the need for scalable, flexible, and efficient storage solutions.

## Rationale
After analyzing and comparing alternatives, we have come to the conclusion that Object Store is the better option because of the following reasons:

**Scalability** : Can easily handle large volumes of resumes and accommodate growth without performance degradation.

**Cost Efficiency**: Generally lower operational costs compared to traditional storage solutions, especially for large data sets.

**Accessibility**: API-driven access allows for easy integration with other components of the HR Orchestrator engine.

## Alternatives Considered
### Alternative 1: Relational Database Management System (RDBMS)
**Pros**: Strong ACID compliance, good for structured data.
**Cons**: Not ideal for large binary files (like resumes), increased complexity in handling non-tabular data.
### Alternative 2: NoSQL Document Store
**Pros**: Good for unstructured data, flexible schema.
**Cons**: May lack some transactional support and could lead to data consistency issues.
