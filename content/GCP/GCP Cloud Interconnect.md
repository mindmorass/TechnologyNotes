---
tags:
  - resource
Area: "[[My Areas]]"
---
### **Explanation of GCP Cloud Interconnect**

- **On-Premises Network** → The customer's **data center or office network**.
- **GCP Interconnect Location** → A **physical location** where Google **provides the Cloud Interconnect**.
- **GCP Virtual Circuit** → The **logical connection** that enables routing between **on-prem** and **GCP**.
- **GCP VPC** → Connects to **GCP resources** over a **dedicated private link**.
- **GCP Cloud Router** → Used for **dynamic BGP routing** to manage **on-prem-to-cloud connectivity**.

```mermaid
flowchart TD
  subgraph "Multi-Region Scope"
    GCP_Cloud_Interconnect["GCP Cloud Interconnect"]:::internal-link
  end

  GCP_On_Premises_Network["On-Premises Network"]:::internal-link
  GCP_Interconnect_Location["GCP Interconnect Location"]:::internal-link
  GCP_Virtual_Circuit["GCP Virtual Circuit"]:::internal-link
  GCP_VPC["GCP VPC"]:::internal-link
  GCP_Cloud_Router["GCP Cloud Router"]:::internal-link

  GCP_On_Premises_Network -->|Dedicated Physical Link| GCP_Cloud_Interconnect
  GCP_Cloud_Interconnect -->|Connection Point| GCP_Interconnect_Location
  GCP_Interconnect_Location -->|Creates Private Link| GCP_Virtual_Circuit
  GCP_Virtual_Circuit -->|Routes Traffic To| GCP_VPC
  GCP_Virtual_Circuit -->|Can Use| GCP_Cloud_Router

```
