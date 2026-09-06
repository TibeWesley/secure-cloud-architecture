````markdown
# Secure Cloud Architecture

## Student Information

**Name:** TIBE WESLEY C.  
**Section:** CCIS7E  
**Course:** BSIT-NETAD  
**Date:** September 6, 2026  

## Project Description

This activity demonstrates a proposed secure cloud architecture for a Student Management Application.

The application is designed to allow users to view student information while keeping important resources protected.

The project focuses on basic cloud networking, security controls, public and private resources, and the Shared Responsibility Model.

## Architecture

The proposed architecture is:

Users → CDN → Load Balancer → Application Servers → Private Database

### Components

- **Users** – People who use the Student Management Application.
- **CDN** – Helps deliver website content faster.
- **Load Balancer** – Distributes user requests between application servers.
- **Application Servers** – Process requests from users.
- **Private Database** – Stores student information and is not directly accessible from the Internet.

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

| Resource | Type |
|---|---|
| CDN | Public |
| Load Balancer | Public |
| Application Server | Private |
| Database | Private |

## Security Approach

The system follows the Principle of Least Privilege.

Users only receive the access they need. Administrator accounts are protected with MFA, and the database is kept private.

The application also uses firewalls, encryption, logging, monitoring, and backups to improve security.

## Repository Files

```text
secure-cloud-architecture/
│
├── index.html
├── README.md
└── security-plan.md
````

## Conclusion

This project demonstrates how a simple cloud application can be designed with security in mind.

The most important idea is that public resources should handle Internet traffic while sensitive resources, such as application servers and databases, should remain private.

```
```
