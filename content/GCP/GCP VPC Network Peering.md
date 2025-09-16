---
tags:
  - resource
Area: "[[My Areas]]"
---
### **Explanation of GCP VPC Network Peering**

- **GCP VPC A & GCP VPC B** → Two **separate VPCs** that want to communicate privately.
- **GCP VPC Network Peering** → Allows **private connectivity** between **two GCP VPCs**, even across **different organizations or projects**.
- **GCP Route Tables (A & B)** → Must be configured to **allow traffic routing** between the peered VPCs.

```mermaid
flowchart TD
  subgraph "Multi-Region Scope"
    GCP_VPC_Network_Peering["GCP VPC Network Peering"]:::internal-link
  end

  GCP_VPC_A["GCP VPC A"]:::internal-link
  GCP_VPC_B["GCP VPC B"]:::internal-link
  GCP_Route_Tables_A["GCP Route Tables (VPC A)"]:::internal-link
  GCP_Route_Tables_B["GCP Route Tables (VPC B)"]:::internal-link

  GCP_VPC_A -->|Establishes Peering Connection| GCP_VPC_Network_Peering
  GCP_VPC_B -->|Establishes Peering Connection| GCP_VPC_Network_Peering
  GCP_VPC_Network_Peering -->|Requires Routing Configuration| GCP_Route_Tables_A
  GCP_VPC_Network_Peering -->|Requires Routing Configuration| GCP_Route_Tables_B

```
