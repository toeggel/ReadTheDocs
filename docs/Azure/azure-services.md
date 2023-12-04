---
tags:
  - Azure
  - Serverless
---
# Azure Services

## Azure Functions vs Azure Logic Apps

Azure Functions is a serverless __compute__ service.

Azure Logic Apps provides serverless __workflows__.

Both can create complex orchestrations. 

> When dealing with synchronous request/response calls, that execute more complex logic, Azure Functions is the preferred option. Logic Apps is better suited for asynchronous integration and fire-and-forget messaging that requires reliable processing. When using Logic Apps, they can be perfectly extended with Azure Functions to execute stateless tasks that cannot be fulfilled by the out-of-the-box Logic Apps capabilities.

|                       | Durable Functions                                                     | Logic Apps                                                                                             |
| --------------------- | --------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| **Development**       | Code-first (imperative)                                               | Designer-first (declarative)                                                                           |
| **Connectivity**      | About a dozen built-in binding types, write code for custom bindings  | Large collection of connectors, Enterprise Integration Pack for B2B scenarios, build custom connectors |
| **Actions**           | Each activity is an Azure function; write code for activity functions | Large collection of ready-made actions                                                                 |
| **Monitoring**        | Azure Application Insights                                            | Azure portal, Azure Monitor logs                                                                       |
| **Management**        | REST API, Visual Studio                                               | Azure portal, REST API, PowerShell, Visual Studio                                                      |
| **Execution context** | Can run locally or in the cloud                                       | Runs only in the cloud                                                                                 |
