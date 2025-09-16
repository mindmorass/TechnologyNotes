---
tags:
  - resource
Area: "[[My Areas]]"
---

### **Explanation of GCP VPC Peering**

- **GCP VPC A & GCP VPC B** → Two **separate VPCs** that want to communicate.
- **GCP VPC Peering** → Allows **private connectivity** between **two VPCs** in **GCP without requiring an external connection**.
- **GCP Route Tables** → Must be configured to allow **traffic between the peered VPCs**.

```mermaid
flowchart TD
  subgraph "Multi-Region Scope"
    GCP_VPC_Peering["GCP VPC Peering"]:::internal-link
  end

  GCP_VPC_A["GCP VPC A"]:::internal-link
  GCP_VPC_B["GCP VPC B"]:::internal-link
  GCP_Route_Tables["GCP Route Tables"]:::internal-link

  GCP_VPC_A -->|Direct Private Connectivity| GCP_VPC_Peering
  GCP_VPC_B -->|Direct Private Connectivity| GCP_VPC_Peering
  GCP_VPC_Peering -->|Requires Routing Configuration| GCP_Route_Tables

```
