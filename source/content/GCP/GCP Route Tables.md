### Explanation of GCP Route Tables

- **GCP Route Tables** → Collections of **routing rules** applied to each VPC network.  
- **Routes** → Define how packets are forwarded (destination CIDR → next hop).  
- **Default Routes** → Every VPC has default routes to the internet (0.0.0.0/0 via default internet gateway) and to internal IP ranges.  
- **Custom Routes** → Added manually or automatically (e.g., via VPC Peering, Shared VPC, Cloud VPN, or Interconnect).  
- **In Peering** → Routes must be **exchanged between peered VPCs** for connectivity to work.  

---

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

### Pages for this diagram
 
- [[GCP VPC Peering]]
- [GCP VPC A](./gcp-vpc-a.md)
- [GCP VPC B](./gcp-vpc-b.md)

---
#### References
#### Official
- https://cloud.google.com/vpc/docs/routes
- https://cloud.google.com/vpc/docs/vpc-peering#routing

#### Third-party
- https://medium.com/google-cloud/understanding-google-cloud-vpc-networking-routes-1d2f9f7c7f67
- https://stackoverflow.com/questions/tagged/google-cloud-networking

