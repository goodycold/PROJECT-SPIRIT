# Security – Project Spirit

## Overview

Project Spirit implements AWS security controls to protect its application infrastructure, restrict network access, and secure communication between application tiers.

## Network Security

- Custom Amazon VPC provides network isolation.
- Web, application, and database resources are deployed in separate subnets.
- Security groups restrict traffic between application components.
- Backend EC2 instance is deployed in a private subnet.
- Amazon RDS is privately accessible and not exposed to the public internet.


## IAM Roles and Instance Permissions

- The IAM role `project3tier` was assigned to the EC2 instances to provide secure access to AWS services without storing long-term access keys on the instances.

### Attached IAM Policies

| Policy | Type | Purpose |
|---|---|---|
| `AmazonEC2RoleforSSM` | AWS Managed | Supports EC2 integration with Systems Manager. |
| `AmazonSSMManagedInstanceCore` | AWS Managed | Provides core permissions for Systems Manager instance management and Session Manager. |

- Database credentials are supplied through environment variables rather than hardcoded in application files.

### Security Benefits

- Enables remote EC2 management through AWS Systems Manager.
- Uses temporary credentials through the EC2 instance role.
- Eliminates the need to store long-term AWS access keys on the instances.
- Supports controlled access to AWS management services.

## Application Security

- AWS Certificate Manager (ACM) provides the SSL/TLS certificate.
- HTTPS is enabled on the external Application Load Balancer.
- HTTP traffic is permanently redirected to HTTPS.
- Apache forwards API requests through the internal Application Load Balancer.
- The backend is not directly exposed to public internet traffic.

## Traffic Protection

The security groups enforce controlled communication:

- Internet → External ALB: HTTP (80) and HTTPS (443).
- External ALB → Web EC2: HTTP (80).
- Web EC2 → Internal ALB: HTTP (80).
- Internal ALB → Backend EC2: HTTP (5000).
- Backend EC2 → Amazon RDS: MySQL (3306).

## Security Objective

The project demonstrates network segmentation, controlled service-to-service communication, IAM-based access, private database connectivity, and HTTPS encryption in an AWS-hosted three-tier application.
