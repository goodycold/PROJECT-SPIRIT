# Load Balancing – Project Spirit

## Overview

Project Spirit uses two Application Load Balancers (ALBs) to distribute application traffic across the web and backend tiers.

## External Application Load Balancer

- **Name:** `PROJECT-SPIRIT-EXTERNAL-LB`
- **Scheme:** Internet-facing
- **Listeners:** HTTP (80) and HTTPS (443)
- **Target Group:** `PROJECT-SPIRIT-WEB-TG`
- **Function:** Receives public requests and forwards traffic to the web tier.
- HTTP traffic is redirected to HTTPS using a permanent 301 redirect.
- HTTPS uses an AWS Certificate Manager (ACM) certificate.

## Internal Application Load Balancer

- **Name:** `PROJECT-APPLICATION-LB`
- **Scheme:** Internal
- **Listener:** HTTP (80)
- **Target Group:** Backend target group
- **Function:** Routes API requests from the web tier to the Flask backend running on EC2.

## Traffic Flow

```text
Internet
   |
   v
External ALB (HTTPS:443)
   |
   v
Web Tier EC2 (Apache)
   |
   v
Internal ALB (HTTP:80)
   |
   v
Backend EC2 (Flask/Gunicorn)
   |
   v
Amazon RDS (MySQL)
```

## Security

- External ALB handles public HTTPS traffic.
- HTTP requests are redirected to HTTPS.
- Internal ALB is not internet-facing.
- Security groups control communication between the load balancers and their respective targets.
- Backend instances are not directly accessible from the public internet.

## Purpose

The two-load-balancer design separates public web traffic from internal API communication, providing controlled traffic routing between the application tiers.
