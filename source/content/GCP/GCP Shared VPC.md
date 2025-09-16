---
tags:
  - resource
Area: "[[My Areas]]"
---
```mermaid
flowchart TD
  subgraph "Multi-Region Scope"
    GCP_Shared_VPC["GCP Shared VPC (Host Project)"]:::internal-link
  end

  GCP_Service_Project_1["GCP Service Project 1"]:::internal-link
  GCP_Service_Project_2["GCP Service Project 2"]:::internal-link

  GCP_Shared_VPC -->|Provides Networking To| GCP_Service_Project_1
  GCP_Shared_VPC -->|Provides Networking To| GCP_Service_Project_2

```
