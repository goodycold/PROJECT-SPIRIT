## Overview

The frontend provides the user interface for Project Spirit, allowing users to submit new records and view previously saved records.

## Technologies

- HTML – Page structure.
- CSS – Styling and layout.
- JavaScript – User interactions and API communication.
- Apache – Web server hosting the frontend.

## Features

- **Add New Record:** Allows users to submit record descriptions.
- **Saved Records:** Displays records retrieved from the backend API.
- **API Integration:** Communicates with the Flask backend through the Apache reverse proxy.

## Deployment & Security 

The frontend is hosted on an Amazon EC2 instance in a public subnet, with inbound HTTP traffic restricted to the external Application Load Balancer's security group.

Apache serves the frontend over the web tier and forwards API requests to the internal Application Load Balancer. Public access is provided through the external ALB using HTTPS, with HTTP requests redirected to HTTPS.

## Live Application

https://project-spirit.site
