# ADR 20: Event-Driven Architecture with Microservices for ClearView System

## Date:
2024-09-30

## Status:
Accepted  

## Context:
The ClearView recruitment system aims to provide a robust, scalable, and high-performing platform that integrates with multiple HRMS systems while leveraging AI LLMs for resume recommendations, candidate scoring, and job matching. The following architectural characteristics are critical for the system:
1. **Scalability** – The system must dynamically handle varying loads, including fluctuating numbers of candidates, job postings, and integrations.
2. **Performance** – Low latency and fast processing are required for real-time AI-driven recommendations, data fetching from HRMS systems, and user interactions.
3. **Interoperability** – The system needs to seamlessly integrate with various HRMS platforms, supporting smooth data exchange and maintaining flexibility for future integrations.

### Decision
We have decided to adopt an architectural style that is primarily **event-driven**, with **microservices** as supporting components for ClearView's recruitment system. This hybrid architecture will provide a flexible and modular approach to meet the system's core requirements.

### Justification

#### 1. **Event-Driven Architecture (EDA)**

An event-driven architecture is chosen as the primary architectural style for the following reasons:

- **Scalability**
    - **Dynamic Workload Handling**: The system can scale by independently scaling event consumers during peak usage, such as when there is a surge in resume submissions or AI processing tasks.
    - **Decoupled Components**: Services operate independently and communicate via events, allowing individual scaling without impacting other parts of the system.

- **Performance**
    - **Real-Time Processing**: EDA supports near real-time processing of events, critical for low-latency resume parsing, candidate scoring, and job matching.
    - **Optimized Resource Utilization**: Resources are used more efficiently since tasks are processed only when events are triggered, reducing unnecessary load.
    - **Minimized Latency**: Asynchronous event processing helps avoid latency associated with synchronous API calls, especially for data synchronization across HRMS platforms.

- **Interoperability**
    - **Seamless Integration with HRMS Systems**: Events facilitate communication between ClearView and various HRMS platforms, standardizing data exchange and processing across disparate systems.
    - **Extensibility for Future Integrations**: New HRMS integrations can be easily added by subscribing to relevant events without disrupting existing workflows.

#### 2. **Microservices Architecture**

Microservices are used to complement the event-driven approach for the following reasons:

- **Scalability**
    - **Independent Service Scaling**: Each microservice can be scaled independently based on specific workload requirements (e.g., scaling AI services for more intensive processing).
    - **Service-Oriented Scalability**: Services can adopt different scaling strategies, optimizing resources based on their usage patterns.

- **Performance**
    - **Optimized Execution**: Services can be fine-tuned and deployed independently, allowing for targeted performance improvements.
    - **Asynchronous Communication**: Services interact asynchronously through events, reducing blocking operations and improving system responsiveness.

- **Interoperability**
    - **Standardized APIs for Integration**: Microservices expose well-defined APIs for external interactions, facilitating consistent data exchange with various HRMS platforms.
    - **Support for Multiple Integration Protocols**: The architecture can accommodate different communication protocols, enhancing flexibility and compatibility.

### Consequences
#### **Positive Impacts**
- **Modular and Resilient Design**: The system can evolve, scale, and recover independently due to the decoupling of services.
- **Enhanced Workflow Orchestration**: Event-driven patterns allow orchestration of complex workflows (e.g., integrating AI scoring, fetching HRMS data, and updating candidate records) with flexibility.
- **Efficient Error Handling and Recovery**: The architecture supports robust error management through event retry mechanisms and fallback strategies.

#### **Negative Impacts**
- **Increased Architectural Complexity**: The combination of EDA and microservices adds complexity to the system, requiring careful design and monitoring.
- **Eventual Consistency**: Due to asynchronous processing, there may be scenarios where data consistency is not immediate, potentially requiring mechanisms to handle stale data.
- **Management Overhead**: Managing distributed services, event streams, and message queues introduces additional operational overhead.

### Alternatives Considered
1. **Monolithic Architecture**: Rejected due to scalability limitations and the lack of modularity needed for integrating multiple HRMS platforms and AI components.
2. **Pure Microservices Architecture**: Rejected because it lacks the real-time event-driven processing capabilities needed for low-latency AI recommendations and flexible workflows.
3. **SOA (Service-Oriented Architecture)**: Rejected as it does not provide the same level of decoupling and real-time processing efficiency as EDA combined with microservices.

### Decision Outcome
The event-driven architecture with microservices approach has been approved for the ClearView recruitment system. This architecture aligns well with the requirements for scalability, performance, and interoperability, ensuring a robust and adaptable system.
