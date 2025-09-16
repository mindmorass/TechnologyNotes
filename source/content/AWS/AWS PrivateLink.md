---
tags:
  - resource
Area: "[[My Areas]]"
---
### **Structure of AWS PrivateLink**

- **AWS VPC (Consumer)**: The VPC that wants to connect privately.
- **AWS PrivateLink**: The secure connection enabling private access.
- **AWS VPC (Service Provider)**: The VPC hosting the service.
- **AWS Network Load Balancer (NLB)**: Routes traffic to the service. (ALB or CLB are conceptually interchangeable)
- **AWS VPC Endpoints**: The mechanism that makes PrivateLink work.

```mermaid
flowchart TD
  AWS_Private_Link["AWS PrivateLink"]:::internal-link

  AWS_VPC_Consumer["AWS VPC (Consumer)"]:::internal-link
  AWS_VPC_Service["AWS VPC (Service Provider)"]:::internal-link
  AWS_NLB["AWS Network Load Balancer"]:::internal-link
  AWS_VPC_Endpoints["AWS VPC Endpoints"]:::internal-link

  AWS_VPC_Consumer -->|Requests Private Access| AWS_Private_Link
  AWS_Private_Link -->|Connects to Service| AWS_VPC_Service
  AWS_Private_Link -->|Traffic Routed Through| AWS_NLB
  AWS_Private_Link -->|Uses Interface Endpoints| AWS_VPC_Endpoints

```
