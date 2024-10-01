# ADR-13: SNS(Simple notification Service) Integration

## Date:
2024-09-30

## Status:
Accepted

## Context:
We aim to integrate componenets  with the SNS Servcie.The goal is a fast processing system which communicates with other components using the AWS SNS software . 


## Decision:
We will implement SNS  as the primary queuing solution for our Clearview application.Improve the overall efficiency.
## Alternatives 
The alternatives considered was using the Rabbitmq. But Rabbit mq features were not suitable what was requirted was low latency and high throughput and SNS is providing these than the fault tolerant queue features offered by Rabbitmq
  
## Consequences:
### PROS:
- SNS is an AWS Mnaged service offeriing and highly compatible with Clearview .
  

### Cons:
- Requires additional cost of the SNS Service.
