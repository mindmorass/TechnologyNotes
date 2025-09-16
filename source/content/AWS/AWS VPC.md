---
tags:
  - resource
Area: "[[My Areas]]"
---

```mermaid
flowchart TD
  AWS_VPC["AWS VPC"]:::internal-link

  AWS_Public_Subnet["AWS Public Subnet"]:::internal-link
  AWS_Private_Subnet["AWS Private Subnet"]:::internal-link

  AWS_Internet_Gateway["AWS Internet Gateway"]:::internal-link
  AWS_NAT_Gateway["AWS NAT Gateway"]:::internal-link

  AWS_Route_Table_Public["AWS Route Table (Public)"]:::internal-link
  AWS_Route_Table_Private["AWS Route Table (Private)"]:::internal-link

  Internet["Internet"]

  %% VPC to subnets
  AWS_VPC -->|Can Contain| AWS_Public_Subnet
  AWS_VPC -->|Can Contain| AWS_Private_Subnet

  %% Subnet uses route table
  AWS_Public_Subnet -->|Uses| AWS_Route_Table_Public
  AWS_Private_Subnet -->|Uses| AWS_Route_Table_Private

  %% Gateway access
  AWS_Public_Subnet -->|Outbound Access| AWS_Internet_Gateway
  AWS_Private_Subnet -->|Private Outbound Access| AWS_NAT_Gateway
  AWS_NAT_Gateway -->|Uses| AWS_Internet_Gateway
  AWS_Internet_Gateway -->|Connects To| Internet

  %% Route table logic with clear context
  AWS_Route_Table_Public -->|"Public Route: 0.0.0.0/0 → IGW"| AWS_Internet_Gateway
  AWS_Route_Table_Private -->|"Private Route: 0.0.0.0/0 → NAT GW"| AWS_NAT_Gateway

```

