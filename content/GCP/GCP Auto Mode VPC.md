---
tags:
  - resource
Area: "[[My Areas]]"
---

```mermaid
flowchart TD
  subgraph "Multi-Region Scope"
    GCP_Auto_Mode_VPC["GCP Auto Mode VPC"]:::internal-link
  end

  subgraph "GCP Regions"
    GCP_Public_Subnet_Region1["GCP Public Subnet (Region 1)"]:::internal-link
    GCP_Private_Subnet_Region1["GCP Private Subnet (Region 1)"]:::internal-link
    GCP_Public_Subnet_Region2["GCP Public Subnet (Region 2)"]:::internal-link
    GCP_Private_Subnet_Region2["GCP Private Subnet (Region 2)"]:::internal-link
  end

  GCP_Auto_Mode_VPC -->|Pre-Created Subnets| GCP_Public_Subnet_Region1
  GCP_Auto_Mode_VPC --> GCP_Private_Subnet_Region1
  GCP_Auto_Mode_VPC --> GCP_Public_Subnet_Region2
  GCP_Auto_Mode_VPC --> GCP_Private_Subnet_Region2

```
