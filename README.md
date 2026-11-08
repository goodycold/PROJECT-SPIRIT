# Project Spirit

### AWS Three-Tier Web Application

[![Live Application](https://img.shields.io/badge/Live%20Application-project--spirit.site-blue)](https://project-spirit.site)

## Overview

Project Spirit is a simple three-tier web application deployed on Amazon Web Services (AWS).

The application allows users to submit record descriptions, store them in a MySQL database, and retrieve previously saved records through a web interface, with the records displayed in  SAVED Records Section 

The project demonstrates AWS infrastructure deployment, network segmentation, application hosting, load balancing, database integration, and secure HTTPS communication.

## Live Application


**Website:** https://project-spirit.site

## Architecture

The infrastructure follows a three-tier architecture:

```text
                    INTERNET
                       |
                       v
             Route 53 (DNS)
                       |
                       v
          External Application Load Balancer
                  HTTPS : 443
                       |
                       v
               Web Tier (EC2)
                  Apache
                       |
                       v
          Internal Application Load Balancer
                    HTTP : 80
                       |
                       v
              Backend Tier (EC2)
                 Flask / Gunicorn
                       |
                       v
                Amazon RDS
                   MySQL
```

### Application Workflow

1. A user submits a record through the web interface.
2. The frontend sends an HTTP request to the Apache web server.
3. Apache forwards the API request to the internal Application Load Balancer.
4. The internal ALB routes the request to the Flask backend running on EC2.
5. Flask processes the request and communicates with Amazon RDS MySQL.
6. The database stores new records or retrieves existing records.
7. The backend returns the response to the frontend, where saved records are displayed.

## AWS Services Used

| AWS Service | Purpose |
|---|---|
| Amazon VPC | Network isolation and segmentation |
| Amazon EC2 | Hosts the frontend and backend |
| Application Load Balancer | Distributes web and API traffic |
| Amazon RDS | Managed MySQL database |
| Amazon Route 53 | Domain name management and DNS routing |
| AWS Certificate Manager | SSL/TLS certificate management |
| Amazon S3 | Stores application source files |
| NAT Gateway | Provides outbound internet access to private application resources |
| IAM | Manages permissions for AWS resources |
| AWS Systems Manager | Remote EC2 instance management |

## Technology Stack

- **Frontend:** HTML, CSS, JavaScript
- **Web Server:** Apache
- **Backend:** Python, Flask, Gunicorn
- **Database:** MySQL 8.4
- **Operating System:** Amazon Linux 2023

## Infrastructure Design

The infrastructure is deployed in a custom VPC in the AWS Stockholm Region (`eu-north-1`).

The VPC uses two Availability Zones and contains six subnets:

- Two public subnets for the web tier and internet-facing load balancer.
- Two private application subnets for backend infrastructure and the internal load balancer.
- Two private database subnets for Amazon RDS.

An Internet Gateway provides connectivity to public resources, while a NAT Gateway enables outbound connectivity from private application resources.

## Security Implementation

The project incorporates several AWS security controls:

- Public, application, and database subnet separation.
- Security groups restricting communication between application tiers.
- Private deployment of the backend EC2 instance and RDS database.
- IAM instance role for controlled AWS service access.
- AWS Systems Manager for remote instance management.
- HTTPS enabled through AWS Certificate Manager.
- HTTP requests redirected to HTTPS using a permanent 301 redirect.
- Internal ALB used for private backend communication.
- Database credentials managed through environment variables.

## Project Features

- Submit new record descriptions.
- Store records in Amazon RDS MySQL.
- Retrieve and display saved records.
- Secure public access through HTTPS.
- Internal routing between application tiers.

## Project Structure

```text
PROJECT-SPIRIT/
│
├── backend/
│   ├── app.py
│   ├── database.py
│   ├── requirements.txt
│   └── README.md
│
├── frontend/
│   ├── index.html
│   ├── css/
│   │   └── style.css
│   ├── js/
│   │   └── app.js
│   └── README.md
│
└── README.md
```

## Project Outcome

Successfully deployed a functional three-tier web application on AWS, integrating EC2, Application Load Balancers, Amazon RDS, VPC networking, Route 53, and AWS Certificate Manager.

The project demonstrates practical experience in cloud infrastructure deployment, application integration, network segmentation, IAM-based access, and HTTPS configuration.

## Author

**Goodluck O. Peters**

Cloud Security Engineering | AWS Infrastructure | Application Security
