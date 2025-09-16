---
tags:
  - resource
  - cloud-platform
  - gcp-networking
Area: "[[My Areas]]"
Platform: "GCP"
Service: "Route Tables"
---

# GCP Route Tables

## Overview

- **GCP Route Tables** → Collections of routing rules that determine how packets are forwarded within and outside VPC networks
- **Key Features** → Automatic system routes, custom route creation, priority-based routing, dynamic route exchange
- **Use Cases** → Traffic steering, hybrid connectivity routing, multi-VPC communication, network segmentation
- **Scope** → Global routing rules applied to VPC networks with regional and zonal specificity
- **Integration** → Works with VPC Peering, Cloud VPN, Cloud Interconnect, and Cloud Router for dynamic routing

---

## Configuration Examples

#### Example Route Table
| Destination CIDR   | Next Hop            | Type          | Notes                                                                 |
|--------------------|---------------------|---------------|----------------------------------------------------------------------|
| 10.0.0.0/8         | Local               | Private       | RFC1918 private range                                                |
| 172.16.0.0/12      | Local               | Private       | RFC1918 private range                                                |
| 192.168.0.0/16     | Local               | Private       | RFC1918 private range                                                |
| 100.64.0.0/10      | Local               | Carrier-Grade | Shared address space (RFC6598, often used for NAT)                   |
| 198.18.0.0/15      | Local/Test          | Benchmarking  | Used for network interconnect testing                                |
| 169.254.0.0/16     | Local-Link          | Link-Local    | Used for automatic IP assignment (APIPA, RFC3927)                    |
| 224.0.0.0/4        | Multicast           | Special       | Reserved for multicast traffic                                       |
| 240.0.0.0/4        | Reserved            | Special       | Reserved for future use (includes 255.255.255.255 broadcast)         |
| 127.0.0.0/8        | Loopback            | Special       | Localhost traffic (127.0.0.1)                                        |
| 0.0.0.0/0          | Internet Gateway    | Default       | Default route to internet (if allowed by firewall/NAT config)        |

---

---

## Related Services

### Core Dependencies
- [[GCP VPC]] - Parent network where routes are applied
- [[GCP Subnets]] - Regional components affected by routing decisions
- **GCP Cloud Router** - Manages dynamic BGP routing for hybrid connectivity

### Routing Integrations
- [[GCP VPC Peering]] - Automatic route exchange between peered VPCs
- [[GCP Cloud VPN]] - Static and dynamic routes for on-premises connectivity
- [[GCP Cloud Interconnect]] - BGP routing for dedicated connections
- **GCP Load Balancers** - Use routes for traffic distribution

### Network Services
- **GCP Firewall Rules** - Applied after routing decisions are made
- **GCP Cloud NAT** - Routes traffic through NAT gateways
- [[GCP Private Service Connect]] - Private service routing

### Cross-Platform Equivalents
| GCP | AWS | Azure | Description |
|-----|-----|-------|-------------|
| Routes | Route Tables | Route Tables | Traffic forwarding rules |
| Cloud Router | BGP Router | Virtual Network Gateway | Dynamic routing |
| System Routes | Local Routes | System Routes | Automatic network routes |
| Custom Routes | Custom Routes | User-defined Routes | Manual routing rules |

---

## References

### Official Documentation
- [Routes Overview](https://cloud.google.com/vpc/docs/routes)
- [VPC Peering Routing](https://cloud.google.com/vpc/docs/vpc-peering#routing)
- [Cloud Router](https://cloud.google.com/network-connectivity/docs/router)
- [Hybrid Connectivity Routing](https://cloud.google.com/hybrid-connectivity/docs/concepts/routing)
- [Route Priorities](https://cloud.google.com/vpc/docs/routes#route-priority)

### Third-Party Resources
- [Medium - GCP Routing Deep Dive](https://medium.com/google-cloud/understanding-google-cloud-vpc-networking-routes-1d2f9f7c7f67)
- [Stack Overflow - GCP Networking](https://stackoverflow.com/questions/tagged/google-cloud-networking)
- [Reddit - GCP Community](https://reddit.com/r/googlecloud)
- [YouTube - GCP Routing Tutorials](https://youtube.com/results?search_query=gcp+routing+tutorial)

### Learning Resources
- [Google Cloud Network Engineer Path](https://cloud.google.com/training/networking)
- [Professional Cloud Network Engineer Certification](https://cloud.google.com/certification/cloud-network-engineer)
- [Advanced Networking Labs](https://cloud.google.com/training/courses/networking-gcp)
- [Routing Best Practices](https://cloud.google.com/architecture/best-practices-vpc-design#routing)

