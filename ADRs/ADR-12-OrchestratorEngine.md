# ADR-12: Orchestration engine for HR system integration

## Date:
2014-09-30

## Status:
Accepted

## Context
The business model charges a fee for sending candidates 'original resumes to employers' HR systems. To support this, the team must build multiple HR system integrations with the flexibility to add more as needed.

## Decision
We decided to develop a custom orchestration engine utilizing available connector and orchestration libraries. This approach allows us to expand without worrying about service limitations. Additionally, Kafka will be used as an event store to handle asynchronous operations.


## Rationale
After evaluating several platforms and services for this workflow with various HR systems, we found none that met our requirements without significant customization or high costs. As a result, building our own orchestration engine provides the flexibility to meet future needs without service constraints.

## Consequences:
### Pros:
- **Full Control and Customization:** We can tailor the system exactly to our needs, with the flexibility to modify, extend, or integrate as required without external restrictions.
- **No Vendor Lock-In:** By developing in-house, we avoid dependency on external vendors and their pricing or business changes.
 - **Enhanced Security and Compliance:** Custom solutions allow for fine-grained control over security and compliance, critical for meeting specific legal or business needs.

### Cons:
- **High Initial Costs:**  Building a custom solution typically requires significant upfront investment in development, infrastructure, and talent.
- **Longer Development Time:**  A custom solution generally takes longer to develop and deploy, potentially delaying time-to-market.
- **Maintenance Burden:**  Continuous support, updates, and scaling must be managed in-house, which adds to operational overhead.


## Alternatives Considered
Here are some popular orchestration and workflow platforms that can help integrate HR systems like SuccessFactors, UKG Pro, Paycor, Workday, Gusto, and others:

- Workato: Offers robust integration and automation for connecting various HR systems, allowing smooth data flow between platforms such as Workday and SuccessFactors.
- MuleSoft: Provides API-based integration solutions, enabling seamless connections with HR systems like UKG Pro and Workday. It also allows for easy management of workflows across different platforms.
- Zapier: Ideal for smaller businesses, Zapier can automate tasks and create workflows between different HR platforms, including Gusto and Paycor.
- Tray.io: A flexible automation platform for integrating enterprise HR systems like SuccessFactors, UKG Pro, and others, offering custom workflow management.

While these platforms offer functionality, they all have limited connectors and require significant customization. Additionally, security concerns arise with sending original resumes, making a custom solution the best fit for our needs.

