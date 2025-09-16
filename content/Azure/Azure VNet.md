---
tags:
  - resource
Area: "[[My Areas]]"
---


```mermaid
flowchart LR
  Azure_VNet["Azure VNet"]:::internal-link

  Azure_VNet_Peering["Azure VNet Peering"]:::internal-link
  Azure_Private_Link["Azure Private Link"]:::internal-link
  Azure_ExpressRoute["Azure ExpressRoute"]:::internal-link
  Azure_VPN_Gateway["Azure VPN Gateway"]:::internal-link
  Azure_Subnet_Public["Azure Public Subnet"]:::internal-link
  Azure_Subnet_Private["Azure Private Subnet"]:::internal-link
  Azure_NSG["Azure Network Security Group"]:::internal-link
  Azure_Route_Table["Azure Route Table"]:::internal-link

  Azure_VNet -->|Contains| Azure_Subnet_Public
  Azure_VNet -->|Contains| Azure_Subnet_Private
  Azure_VNet -->|Applies Traffic Filtering| Azure_NSG
  Azure_VNet -->|Controls Routing| Azure_Route_Table

  Azure_VNet -->|Direct Peer Connection| Azure_VNet_Peering
  Azure_VNet -->|Private Access to Azure Services| Azure_Private_Link
  Azure_VNet -->|Dedicated Private Connection| Azure_ExpressRoute
  Azure_VNet -->|VPN Connectivity| Azure_VPN_Gateway

```

## Documentation
* https://learn.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview


#flashcards/azure
What Services are available under VNet
?
- Public Subnet(s)
- Private Subnet(s)
- Network Security Group(s)
- Route Table
- VNet Peering
- Private Link
- ExpressRoute
- VPN. Gateway