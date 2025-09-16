---
tags:
  - resource
Area: "[[My Areas]]"
---
### **Structure of AWS Transit Gateway**

- **AWS Transit Gateway** acts as a central router for multiple **AWS VPCs**.
- **AWS Direct Connect** provides a dedicated private link to on-premises.
- **AWS Site-to-Site VPN** allows secure VPN connections to on-prem.

```mermaid
flowchart TD
  AWS_Transit_Gateway["AWS Transit Gateway"]:::internal-link

  AWS_VPC_A["AWS VPC A"]:::internal-link
  AWS_VPC_B["AWS VPC B"]:::internal-link
  AWS_VPC_C["AWS VPC C"]:::internal-link
  AWS_Direct_Connect["AWS Direct Connect"]:::internal-link
  AWS_Site_To_Site_VPN["AWS Site-to-Site VPN"]:::internal-link

  AWS_Transit_Gateway -->|Centralized Routing| AWS_VPC_A
  AWS_Transit_Gateway -->|Centralized Routing| AWS_VPC_B
  AWS_Transit_Gateway -->|Centralized Routing| AWS_VPC_C
  AWS_Transit_Gateway -->|On-Premises Connectivity| AWS_Direct_Connect
  AWS_Transit_Gateway -->|VPN Connectivity| AWS_Site_To_Site_VPN

```


## Subgraphs
- [[AWS Direct Connect]]
- 