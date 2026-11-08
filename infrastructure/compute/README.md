# Compute – Amazon EC2

## Overview

Project Spirit uses Amazon EC2 instances to host the web and backend application tiers.

## Web Tier – WEBSERVER-INSTANCE

- **Service:** Amazon EC2
- **Operating System:** Amazon Linux 2023
- **Web Server:** Apache
- **Subnet:** Public subnet
- **Function:** Hosts the frontend application and forwards API requests to the internal Application Load Balancer.

## Backend Tier – PROJECTAPP-INSTANCE

- **Service:** Amazon EC2
- **Operating System:** Amazon Linux 2023
- **Runtime:** Python
- **Framework:** Flask
- **WSGI Server:** Gunicorn
- **Subnet:** Private application subnet
- **Port:** 5000
- **Function:** Processes API requests and communicates with Amazon RDS MySQL.

## Instance Management

AWS Systems Manager (SSM) provides remote instance management without requiring direct SSH access.

The backend runs as a systemd service, allowing automatic startup and restart management.

## Security

- Web and backend instances are deployed in separate network tiers.
- Backend EC2 does not have direct public internet exposure.
- Security groups restrict inbound traffic to authorized application components.
- The web tier receives public traffic through the external Application Load Balancer.
- The backend receives API traffic through the internal Application Load Balancer.

## Purpose

The EC2 instances provide the compute infrastructure for hosting the frontend and backend components while maintaining separation between the application tiers.
