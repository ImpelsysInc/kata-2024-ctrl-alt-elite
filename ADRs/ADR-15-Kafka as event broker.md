# ADR-015: Event Broker using Kafka 

## Date:
2024-09-30

## Status:
Accepted

## Context: 
Implementing Event Broker for Event-Driven Architecture.The system is designed with an event-driven architecture where different components need to intereact to various application events (such as user actions, system events, and data processing). To ensure efficient communication between these services, we require a scalable, fault-tolerant, and high-throughput

## Decision:
We will use Apache Kafka as the event broker for handling real-time event streaming and communication between microservices in the application.


## Alternatives
Considered Options:
RabbitMQ
Pros:
Simple setup and configuration.
Supports various messaging protocols.
Good for complex routing and message queuing.
Cons:
Limited scalability compared to Kafka for large-scale event streaming.
Lower throughput for large, real-time data processing tasks.

AWS SQS/SNS
Pros:
Fully managed service; minimal operational overhead.
Highly scalable and reliable.
Cons:
Does not support true real-time event streaming like Kafka.
More suitable for message queuing than high-throughput streaming.

## Consequences: Using Kafka as a event broker
### Pros:
Distributed, scalable, and fault-tolerant.
High throughput and low latency.
Strong support for stream processing.
Widely adopted and has a strong community.
## Cons:
Operational complexity, requires more effort to manage and monitor.
Message ordering is only guaranteed per partition.
