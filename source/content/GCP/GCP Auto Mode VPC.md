---
tags:
  - resource
  - cloud-platform
  - gcp-networking
Area: "[[My Areas]]"
Platform: "GCP"
Service: "Auto Mode VPC"
---

# GCP Auto Mode VPC

## Overview

- **GCP Auto Mode VPC** → VPC that automatically creates subnets in each GCP region with predefined IP ranges
- **Key Features** → Automatic subnet creation, predefined IP ranges, simple setup, regional coverage
- **Use Cases** → Quick prototyping, simple applications, getting started with GCP, development environments
- **Scope** → Global VPC with automatic regional subnet creation
- **Integration** → Suitable for basic compute workloads, simple multi-region deployments

---

## Architecture Diagram

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

---

## Configuration Examples

### Auto Mode VPC Characteristics
| Feature | Value | Description | Configurable |
|---------|-------|-------------|-------------|
| Subnet Creation | Automatic | Subnets created in all regions | No |
| IP Range | `10.128.0.0/9` | Predefined CIDR block | No |
| Subnet Size | `/20` per region | 4096 IP addresses per region | No |
| Mode Conversion | Supported | Can convert to custom mode | Yes |

### Basic Configuration
```yaml
# Creating an auto mode VPC
auto_vpc:
  name: "auto-mode-network"
  subnet_mode: "auto"
  description: "Automatically created subnets in all regions"
  # Subnets are automatically created with:
  # us-central1: 10.128.0.0/20
  # us-east1: 10.142.0.0/20
  # europe-west1: 10.132.0.0/20
  # etc.
```

### gcloud Commands
```bash
# Create auto mode VPC (subnets created automatically)
gcloud compute networks create auto-mode-network \
    --subnet-mode=auto \
    --bgp-routing-mode=regional \
    --description="Automatically created subnets in all regions"

# List automatically created subnets
gcloud compute networks subnets list --filter="network:auto-mode-network"

# Convert auto mode to custom mode (one-way operation)
gcloud compute networks update auto-mode-network \
    --switch-to-custom-subnet-mode

# Add custom subnet after conversion to custom mode
gcloud compute networks subnets create custom-subnet \
    --network=auto-mode-network \
    --range=172.16.0.0/24 \
    --region=us-west1 \
    --enable-private-ip-google-access

# Create firewall rule for auto mode VPC
gcloud compute firewall-rules create allow-internal-auto \
    --network=auto-mode-network \
    --allow=tcp,udp,icmp \
    --source-ranges=10.128.0.0/9 \
    --description="Allow communication between auto-created subnets"

# Create firewall rule for SSH access
gcloud compute firewall-rules create allow-ssh-auto \
    --network=auto-mode-network \
    --allow=tcp:22 \
    --source-ranges=0.0.0.0/0 \
    --target-tags=ssh-enabled

# Create firewall rule for HTTP/HTTPS
gcloud compute firewall-rules create allow-http-https-auto \
    --network=auto-mode-network \
    --allow=tcp:80,tcp:443 \
    --source-ranges=0.0.0.0/0 \
    --target-tags=web-server

# Describe the auto mode network
gcloud compute networks describe auto-mode-network

# Delete auto mode VPC (must delete all resources first)
gcloud compute networks delete auto-mode-network
```

---

## Related Services

### Core Dependencies
- [[GCP VPC]] - Base VPC networking concepts
- [[GCP Subnets]] - Automatically created regional subnets
- **GCP Firewall Rules** - Default and custom security rules

### VPC Alternatives
- [[GCP Custom Mode VPC]] - Manually configured subnets and IP ranges
- [[GCP Shared VPC]] - Network sharing across projects

### Migration Path
- **VPC Mode Conversion** - Convert auto mode to custom mode (one-way)
- **Subnet Management** - Add custom subnets after conversion
- **IP Planning** - Consider future IP requirements

### Cross-Platform Equivalents
| GCP | AWS | Azure | Description |
|-----|-----|-------|-------------|
| Auto Mode VPC | Default VPC | Default Virtual Network | Automatically configured network |
| Auto Subnets | Default Subnets | Default Subnets | Pre-created regional ranges |
| Mode Conversion | VPC Migration | Network Reconfiguration | Changing network setup |

---

## References

### Official Documentation
- [Auto Mode VPC Networks](https://cloud.google.com/vpc/docs/vpc#auto-mode-considerations)
- [VPC Network Modes](https://cloud.google.com/vpc/docs/vpc#network-types)
- [Converting to Custom Mode](https://cloud.google.com/vpc/docs/using-vpc#convert-auto-to-custom)
- [Default Network Behavior](https://cloud.google.com/vpc/docs/vpc#default-network)
- [VPC Pricing](https://cloud.google.com/vpc/pricing)

### Third-Party Resources
- [Stack Overflow - GCP VPC Modes](https://stackoverflow.com/questions/tagged/google-cloud-vpc)
- [Medium - GCP Networking Basics](https://medium.com/tag/gcp-networking)
- [Reddit - GCP Community](https://reddit.com/r/googlecloud)
- [YouTube - GCP VPC Tutorials](https://youtube.com/results?search_query=gcp+auto+mode+vpc)

### Learning Resources
- [Google Cloud Fundamentals](https://cloud.google.com/training/courses#cloud-fundamentals)
- [Networking in Google Cloud](https://cloud.google.com/training/courses/networking-gcp)
- [Getting Started Guide](https://cloud.google.com/docs/get-started)
- [Best Practices for VPC Design](https://cloud.google.com/architecture/best-practices-vpc-design)
