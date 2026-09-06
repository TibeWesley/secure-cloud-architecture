# Secure Cloud Architecture

## Student Information

Name: [Your Name]  
Section: [Your Section]  
Course: [Your Course]  
Date: September 6, 2026

## Project Description

This activity demonstrates a proposed secure cloud architecture for a Student Management Application.

The application allows users to view student information while applying basic cloud networking and security concepts.

## Architecture

Users → CDN → Load Balancer → Application Servers → Private Database

The application uses two application servers to improve availability.

## Architecture Components

- Users
- CDN
- Load Balancer
- Application Server 1
- Application Server 2
- Private Database

## Security Controls

- IAM
- MFA
- Firewall / Security Groups
- Private Subnets
- Encryption
- Logging
- Monitoring
- Backups

## Public and Private Resources

The CDN and Load Balancer are public-facing resources.

The Application Servers and Database are private resources.

The database is not directly accessible from the Internet.

## Shared Responsibility Model

The cloud provider is responsible for the security of the underlying cloud infrastructure, including physical data centers and physical servers.

The customer is responsible for security within the cloud environment, including user accounts, IAM permissions, student data, application security, database access rules, and backups.

## Repository Structure

```text
secure-cloud-architecture/
│
├── index.html
├── README.md
└── security-plan.md
