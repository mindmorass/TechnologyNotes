---
tags:
  - resource
Area: "[[My Areas]]"
---

```mermaid
flowchart TD
  Azure_VNet["Azure VNet"]:::internal-link

  Azure_VNet_Peering["Azure VNet Peering"]:::internal-link
  Azure_Private_Link["Azure Private Link"]:::internal-link
  Azure_ExpressRoute["Azure ExpressRoute"]:::internal-link
  Azure_VPN_Gateway["Azure VPN Gateway"]:::internal-link

  Azure_VNet -->|Direct Peer Connection| Azure_VNet_Peering
  Azure_VNet -->|Private Access to Azure Services| Azure_Private_Link
  Azure_VNet -->|Dedicated Private Connection| Azure_ExpressRoute
  Azure_VNet -->|VPN Connectivity| Azure_VPN_Gateway

```

