# ADR-12: Orchestrator Engine Integration using Kafka 

## Date:
2024-09-30

## Status:
Accepted

## Context:
We aim to streamline HR Job posting by integrating Clearview with various applications through Orchestrator engine. The goal is to automate repetitive tasks, enhance data accuracy, and improve the overall efficiency of job posting and status update.

## Decision:
We will implement Orcherstrator Engine(Kafka) as the primary integration solution for our Clearview application.

## Consequences:
### PROS:
- Wide Range of Integrations: Supports numerous HR and business applications, enabling seamless workflows.
- Rapid Deployment: Quick setup allows for immediate benefits, reducing the time to value.
- Pub Sub Model helps in quick ingestion of data from disparate HR Systems 
-  Scalability Kafka is scalable and hence will support as the numnber of organizations as they grow

### Cons:
- Complexity: While Kafka simplifies many aspects of communication, managing a Kafka cluster and ensuring proper data flow can introduce complexity.
- Latency: In scenarios requiring low-latency responses, Kafka's design may not always meet the strict timing requirements.
