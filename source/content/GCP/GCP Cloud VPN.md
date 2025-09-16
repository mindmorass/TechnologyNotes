---
tags:
  - resource
Area: "[[My Areas]]"
---
### **Explanation of GCP Cloud VPN**

- **On-Premises Network** → The customer’s **data center or office network**.
- **GCP Cloud VPN** → Provides an **encrypted tunnel** between **on-prem and GCP** over the internet or a private link.
- **GCP VPN Gateway** → The **endpoint in GCP** where the VPN tunnel terminates.
- **GCP VPN Tunnel** → The **secure tunnel** that encrypts traffic between networks.
- **GCP VPC** → Connects to **GCP resources** via the VPN tunnel.
- **GCP Cloud Router** → **Optional** for **dynamic BGP routing** instead of static routes.

```mermaid
flowchart TD
  subgraph "Multi-Region Scope"
    GCP_Cloud_VPN["GCP Cloud VPN"]:::internal-link
  end

  GCP_On_Premises_Network["On-Premises Network"]:::internal-link
  GCP_VPN_Gateway["GCP VPN Gateway"]:::internal-link
  GCP_Tunnel["GCP VPN Tunnel"]:::internal-link
  GCP_VPC["GCP VPC"]:::internal-link
  GCP_Cloud_Router["GCP Cloud Router"]:::internal-link

  GCP_On_Premises_Network -->|Encrypted Connection| GCP_Cloud_VPN
  GCP_Cloud_VPN -->|Terminates VPN Traffic| GCP_VPN_Gateway
  GCP_VPN_Gateway -->|Secures Traffic| GCP_Tunnel
  GCP_Tunnel -->|Routes Traffic To| GCP_VPC
  GCP_Tunnel -->|Can Use| GCP_Cloud_Router

```

[[[GCP Cloud VPN]]]