---
tags:
  - resource
Area:
---
- [[Networking Concepts]]
- https://aws.amazon.com/products/networking/

### **Structure of AWS VPC Peering**

- **AWS VPC A & AWS VPC B**: Two VPCs wanting to connect.
- **AWS VPC Peering**: Enables private communication between them.
- **AWS Route Tables**: Must be updated to allow traffic routing.


```mermaid
flowchart LR
  AWS_VPC["AWS VPC"]:::internal-link

  AWS_Transit_Gateway["AWS Transit Gateway"]:::internal-link
  AWS_Private_Link["AWS PrivateLink"]:::internal-link
  AWS_VPC_Peering["AWS VPC Peering"]:::internal-link
  AWS_Direct_Connect["AWS Direct Connect"]:::internal-link
  AWS_VPC_Endpoints["AWS VPC Endpoints"]:::internal-link

  AWS_VPC -->|Centralized Routing| AWS_Transit_Gateway
  AWS_VPC -->|Private Access to AWS Services| AWS_Private_Link
  AWS_VPC -->|One-to-One VPC Connection| AWS_VPC_Peering
  AWS_VPC -->|Dedicated Private Connection| AWS_Direct_Connect
  AWS_VPC -->|Private Access to AWS Services| AWS_VPC_Endpoints
```

## Subgraphs

- [[AWS VPC]]
- [[AWS PrivateLink]]
- [[AWS VPC Peering]]
- [[AWS Direct Connect]]
- [[AWS VPC Endpoints]]

