

## Overview

This module manages the connection between the Flask backend and the Amazon RDS MySQL database.

## Responsibilities

- Establishes database connections using environment variables.
- Executes SQL queries for application records.
- Supports inserting new records and retrieving saved records.
- Handles database connection and query operations.

## Database Configuration

The connection uses environment variables to keep database credentials separate from the application source code.

**Database:** MySQL  
**Hosting:** Amazon RDS  
**Database name:** `project_spirit`  
**Table:** `records`

## Security

Database credentials are not hardcoded in the source code or committed to GitHub. Database access is restricted through AWS security groups.
