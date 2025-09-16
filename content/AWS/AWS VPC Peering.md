---
tags:
  - resource
Area: "[[My Areas]]"
---
```mermaid
flowchart TD
  AWS_VPC_Peering["AWS VPC Peering"]:::internal-link

  AWS_VPC_A["AWS VPC A"]:::internal-link
  AWS_VPC_B["AWS VPC B"]:::internal-link
  AWS_Route_Tables["AWS Route Tables"]:::internal-link

  AWS_VPC_A -->|Direct Private Connectivity| AWS_VPC_Peering
  AWS_VPC_B -->|Direct Private Connectivity| AWS_VPC_Peering
  AWS_VPC_Peering -->|Requires Routing Configuration| AWS_Route_Tables

```
