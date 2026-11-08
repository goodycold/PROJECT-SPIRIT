# Networking – Amazon VPC

## Overview

Project Spirit uses a custom Amazon Virtual Private Cloud (VPC) to provide an isolated network environment for hosting its three-tier application infrastructure.

## VPC Configuration

- **VPC Name:** `project-spirit-vpc`
- **CIDR Block:** `10.0.0.0/16`
- **Region:** `eu-north-1` (Stockholm)
- **Availability Zones:** `eu-north-1a` and `eu-north-1b`

## Subnet Architecture

The VPC is divided into three subnet tiers:

| Subnet Tier | Purpose |
|---|---|
| Public Subnets | Host the external Application Load Balancer and web server EC2 instance. |
| Private Application Subnets | Host the backend EC2 instance and internal Application Load Balancer. |
| Private Database Subnets | Provide network isolation for Amazon RDS MySQL. |

Two public, two private application, and two private database subnets are distributed across two Availability Zones.

## Routing and Connectivity

- Internet Gateway provides internet connectivity to public subnets.
- NAT Gateway enables outbound internet access from private application subnets.
- Route tables control traffic between subnets and external networks.
- Private database subnets do not have direct internet access.

## Security

- Network segmentation separates web, application, and database resources.
- Security groups control inbound and outbound traffic.
- Backend and database resources are not directly exposed to the public internet.
- The internal Application Load Balancer handles private application-tier communication.

## Purpose

The VPC architecture provides network isolation, subnet segmentation, controlled connectivity, and separation of the three application tiers across two Availability Zones.
