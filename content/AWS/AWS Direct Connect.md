---
tags:
  - resource
Area: "[[My Areas]]"
---
### **Structure of AWS Direct Connect**

- **On-Premises Network**: The customer's data center or office network.
- **AWS Direct Connect Location**: The physical location where AWS provides Direct Connect.
- **AWS Virtual Interface**: The logical connection that enables routing.
- **AWS VPC**: Direct connection to AWS resources.
- **AWS Transit Gateway**: Optionally used for connecting multiple VPCs.

```mermaid
flowchart TD
  AWS_On_Premises_Network["AWS On-Premises Network"]:::internal-link
  AWS_Direct_Connect["AWS Direct Connect"]:::internal-link
  AWS_DX_Location["AWS Direct Connect Location"]:::internal-link
  AWS_Virtual_Interface["AWS Virtual Interface"]:::internal-link
  AWS_VPC["AWS VPC"]:::internal-link
  AWS_Transit_Gateway["AWS Transit Gateway"]:::internal-link

  AWS_On_Premises_Network -->|Physical Connection| AWS_Direct_Connect
  AWS_Direct_Connect -->|Connects To| AWS_DX_Location
  AWS_DX_Location -->|Creates Private Link| AWS_Virtual_Interface
  AWS_Virtual_Interface -->|Routes Traffic To| AWS_VPC
  AWS_Virtual_Interface -->|Can Also Connect To| AWS_Transit_Gateway

```

## Subgraphs
* [[AWS VPC]]
* [[AWS Direct Connect]]
* [[AWS Transit Gateway]]
