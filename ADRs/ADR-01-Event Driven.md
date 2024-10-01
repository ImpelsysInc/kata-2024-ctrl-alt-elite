

# ADR-01: Event-Driven Architecture

## Date:
2024-09-29

## Status:
Accepted

## Context:
The ClearView platform must efficiently process candidate actions like uploading resumes, updating profiles, searching for jobs, and accessing career tips. These tasks must be handled in near real-time to ensure a smooth and efficient user experience. Similarly, the platform must also handle employer actions, such as searching for candidates, updating job postings, and exploring tips, with the same real-time responsiveness to meet business demands.

## Decision:
We will implement an **Event-Driven Architecture (EDA)** to decouple services and facilitate real-time communication across the platform's services and components.

### Drivers:
- **Scalability**: The platform needs to support growing volumes of candidates, employers, resumes, jobs, and job matching requests.
- **Decoupling**: Services like job management, resume processing, and job matching should function independently, enabling easier updates and enhanced fault tolerance.
- **Real-Time Processing**: Both candidates and employers expect immediate responses after performing actions on the platform.

### Scenarios:
- When a candidate uploads a resume, the application generates an event (e.g., `ResumeUploadedEvent`) with the file details.
- This event is published to an event broker, where other components (e.g., Resume Parser, Job Matcher) subscribe to and process the event accordingly.
- After the `ResumeUploadedEvent` is handled, subsequent events, such as `ResumeParsed` and `StoryCreated`, can trigger further processing by related services.

## Consequences:

### Pros:
- **Scalability**: Individual services can scale independently, handling varying loads without impacting others.
- **Loose Coupling**: Microservices are decoupled, allowing for independent development, updates, and deployments.
- **Improved Responsiveness**: User actions are processed in near real-time, improving the overall user experience.
- **Enhanced Fault Tolerance**: The system can continue functioning even if some services experience temporary downtime.

### Cons:
- **Increased Complexity**: The overall system becomes more complex, requiring robust monitoring and logging infrastructure.
- **Eventual Consistency**: Data consistency across services may not be immediate, requiring careful management of business processes.
- **Learning Curve**: Development teams may need training to fully understand and utilize EDA principles and tools effectively.
