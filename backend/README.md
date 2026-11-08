# Project Spirit – Backend

## Overview

The Project Spirit backend provides the application programming interface (API) responsible for processing requests from the frontend and interacting with the MySQL database.

It is built with Python and Flask and deployed on an Amazon EC2 instance in a private application subnet within a custom AWS VPC.

The backend communicates with the frontend through an internal Application Load Balancer (ALB), while storing application records in Amazon RDS.

## Architecture

The backend follows this request flow:

1. A user submits a record through the web interface.
2. The frontend sends an HTTP request to the Apache web server.
3. Apache forwards the API request through the internal Application Load Balancer.
4. The internal ALB routes the request to the Flask backend running on EC2.
5. Flask processes the request and communicates with Amazon RDS.
6. The database stores or retrieves the requested records.
7. The backend returns the response through the internal ALB and Apache to the frontend, where the result is displayed in the Saved Records section.
   

```text
User Browser
     |
     v
External Application Load Balancer
     |
     v
Web Tier (Apache)
     |
     v
Internal Application Load Balancer
     |
     v
Backend EC2 (Flask + Gunicorn)
     |
     v
Amazon RDS (MySQL)
```

## Technologies Used

- **Python** – Backend programming language.
- **Flask** – Lightweight web framework for API development.
- **Gunicorn** – WSGI server used to run the Flask application.
- **Amazon EC2** – Hosts the backend application.
- **Amazon RDS** – Managed MySQL database service.
- **Amazon VPC** – Provides network isolation.
- **Internal Application Load Balancer** – Routes requests to the backend instance.
- **AWS Systems Manager (SSM)** – Provides instance management access.

## Project Structure

```text
backend/
├── app.py
├── database.py
├── requirements.txt
└── README.md
```

## API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/health` | Checks backend application health. |
| GET | `/api/records` | Retrieves stored records. |
| POST | `/api/records` | Creates and stores a new record. |

### Health Check

The `/health` endpoint is used by the internal Application Load Balancer to verify backend availability.

Example response:

```json
{
  "status": "healthy"
}
```

## Database Integration

The backend connects to an Amazon RDS MySQL database hosted within the private database subnets.

The application uses database connection settings supplied through environment variables.

Database details:

- Database engine: MySQL 8.4
- Database name: `project_spirit`
- Table: `records`
- Port: `3306`

The `records` table stores application descriptions and associated record information.


## Deployment

The backend is deployed on an Amazon Linux 2023 EC2 instance in a private application subnet.

Gunicorn runs the Flask application on port `5000`, while a systemd service manages the application process and enables automatic startup after instance reboots.

The backend is not directly exposed to the public internet. Requests are routed through the internal Application Load Balancer.

## Security Configuration

The backend deployment incorporates the following security controls:

- Backend EC2 instance deployed in a private subnet.
- No direct public internet access to the backend.
- Security group restricts inbound application traffic to the internal ALB.
- Database security group permits MySQL traffic from the backend security group.
- AWS Systems Manager used for instance administration.
- Environment variables used for database configuration.
- Public application traffic enters through the external ALB over HTTPS.
