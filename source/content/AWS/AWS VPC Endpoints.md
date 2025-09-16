---
tags:
  - resource
Area: "[[My Areas]]"
---
### **Structure of AWS VPC Endpoints**

- **AWS VPC Endpoints** allow private access to AWS services **without needing an internet gateway**.
- **AWS Interface Endpoint**: Uses **AWS PrivateLink** to connect to services like EC2, API Gateway, and others.
- **AWS Gateway Endpoint**: Directly routes **S3 and DynamoDB** traffic through VPC without internet access.

```mermaid
flowchart TD
  AWS_VPC_Endpoints["AWS VPC Endpoints"]:::internal-link

  AWS_VPC["AWS VPC"]:::internal-link
  AWS_Interface_Endpoint["AWS Interface Endpoint"]:::internal-link
  AWS_Gateway_Endpoint["AWS Gateway Endpoint"]:::internal-link
  AWS_S3["AWS S3"]:::internal-link
  AWS_DynamoDB["AWS DynamoDB"]:::internal-link
  AWS_PrivateLink["AWS PrivateLink"]:::internal-link

  AWS_VPC -->|Uses| AWS_VPC_Endpoints
  AWS_VPC_Endpoints -->|For AWS Services| AWS_Interface_Endpoint
  AWS_VPC_Endpoints -->|For AWS Services| AWS_Gateway_Endpoint

  AWS_Interface_Endpoint -->|Uses AWS PrivateLink| AWS_PrivateLink
  AWS_Gateway_Endpoint -->|Direct Route in VPC| AWS_S3
  AWS_Gateway_Endpoint -->|Direct Route in VPC| AWS_DynamoDB

```


## Subgraphs

- [[AWS VPC]]
- [[AWS PrivateLink]]
- 