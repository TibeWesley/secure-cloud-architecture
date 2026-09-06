# Secure Cloud Architecture Plan

## Architecture Overview

The proposed Student Management Application uses a layered cloud architecture designed to improve security, availability, and performance.

The basic architecture is:

Users  
↓  
CDN  
↓  
Load Balancer  
↓  
Application Servers  
↓  
Private Database

Two application servers are proposed to improve availability.

Users
↓
CDN
↓
Load Balancer
↓
Application Server 1
Application Server 2
↓
Private Database

---

# Cloud Architecture Components

## Users

Users access the Student Management Application through the Internet using a web browser.

Users should not have direct access to the private database. All requests should pass through the application's secure layers.

## CDN

The Content Delivery Network (CDN) stores cached copies of static content such as HTML, CSS, JavaScript, and images.

The CDN improves website performance by delivering content from locations closer to users.

It can also provide additional security features such as HTTPS support and protection against certain types of attacks.

## Load Balancer

The load balancer distributes incoming requests across multiple application servers.

This prevents one application server from receiving all the traffic.

The load balancer also improves availability because traffic can be redirected to another application server if one server fails.

## Application Servers

Application servers process requests from users and communicate with the database when necessary.

The application servers should be placed in a private subnet.

They should not be directly accessible from the public Internet.

Only the load balancer should be allowed to communicate with the application servers.

## Database

The database stores student information such as student numbers, names, courses, year levels, and email addresses.

The database should remain in a private subnet.

It should not have a public IP address and should not be directly accessible from the Internet.

Only authorized application servers should be allowed to connect to the database.

---

# Public and Private Resources

| Resource | Public or Private? | Explanation |
|---|---|---|
| CDN | Public | The CDN delivers web content to users through the Internet. |
| Load Balancer | Public | The load balancer needs to receive incoming requests from users. |
| Application Server | Private | Application servers should not be directly accessible from the Internet. |
| Database | Private | The database contains student information and should only be accessible by authorized application servers. |

---

# Security Controls

## IAM

Identity and Access Management (IAM) controls who can access the cloud environment.

Only authorized administrators should have administrative access.

Users should receive only the permissions required to perform their responsibilities.

Different roles should be created for administrators, instructors, students, and developers.

Administrative permissions should not be given to normal users.

## MFA

Multi-Factor Authentication (MFA) should be enabled for administrator accounts and other accounts with sensitive privileges.

MFA provides an additional layer of protection if a password is stolen.

Administrators should be required to provide a second authentication factor when accessing the cloud environment.

## Firewall / Security Group

Firewall and security group rules should restrict network traffic.

The following connections should be allowed:

- Internet → CDN = Allowed
- Internet → Load Balancer = Allowed
- CDN → Load Balancer = Allowed
- Load Balancer → Application Server = Allowed
- Application Server → Database = Allowed

The following connection should be blocked:

- Internet → Database = Blocked

The database should only accept connections from authorized application servers.

## Encryption

Student information should be encrypted to protect it from unauthorized access.

Data should be encrypted while being transmitted using HTTPS/TLS.

Sensitive data stored in the database should also be encrypted at rest.

Encryption helps protect student information if network traffic or stored data is exposed.

## Logging

Logging records important activities occurring within the cloud environment and application.

The system should record activities such as:

- User login attempts
- Successful logins
- Failed login attempts
- Administrative actions
- Database access
- Security configuration changes
- Application errors

Logs can help identify security incidents and investigate suspicious activities.

## Monitoring

The system should monitor the cloud environment for unusual or suspicious activity.

Examples include:

- Multiple failed login attempts
- Unusual network traffic
- Unauthorized access attempts
- Unexpected database activity
- High server resource usage
- Changes to security settings

Monitoring allows administrators to detect potential security problems quickly.

## Backup

The database should have regular backups to prevent permanent data loss.

Backups can help recover student records after accidental deletion, system failures, data corruption, or security incidents.

Backups should be stored securely and access to them should be restricted.

---

# Principle of Least Privilege

The Principle of Least Privilege means that users should receive only the permissions required to perform their assigned tasks.

| User | Allowed Access |
|---|---|
| Administrator | Full management access to the cloud environment, security settings, users, application servers, and database administration. |
| Instructor | View authorized student records and perform instructor-related functions. No cloud infrastructure administration. |
| Student | View their own authorized student information. No access to other students' private records or cloud infrastructure. |
| Developer | Access application development resources and application servers when required. No unnecessary access to production student data or administrative security settings. |

Administrator access should not be given to every employee because excessive privileges increase the risk of accidental or unauthorized changes.

---

# Shared Responsibility Model

The Shared Responsibility Model means that cloud security responsibilities are divided between the cloud provider and the customer.

| Responsibility | Cloud Provider or Customer? |
|---|---|
| Physical data center | Cloud Provider |
| Physical servers | Cloud Provider |
| User accounts | Customer |
| Student data | Customer |
| IAM permissions | Customer |
| Application security | Customer |
| Database access rules | Customer |
| Backups | Customer |

## What does Security OF the Cloud mean?

Security OF the Cloud refers to the security responsibilities handled by the cloud provider.

This includes protecting the physical data centers, physical servers, networking infrastructure, and underlying cloud infrastructure.

## What does Security IN the Cloud mean?

Security IN the Cloud refers to the customer's responsibility for protecting what they deploy and configure in the cloud.

This includes user accounts, IAM permissions, application security, student data, database access rules, encryption, and appropriate backups.

---

# Architecture Questions

## 1. Which resource should be directly accessible from the Internet?

The CDN and public-facing load balancer should be accessible from the Internet.

Users should access the application through these public-facing services rather than connecting directly to application servers or the database.

## 2. Why should the database remain private?

The database contains sensitive student information.

Keeping the database private reduces the possibility of unauthorized Internet access and limits the attack surface.

## 3. Why should users not connect directly to the database?

Users should not connect directly to the database because this could expose sensitive information and database credentials.

Instead, users should communicate with the application through the application servers.

## 4. What is the purpose of a load balancer?

The load balancer distributes incoming requests across multiple application servers.

This improves performance and availability.

## 5. What happens if one application server fails?

If one application server fails, the load balancer can stop sending traffic to the failed server and send requests to the remaining healthy application server.

This helps keep the application available.

## 6. What is the purpose of a CDN?

The CDN delivers cached web content from locations closer to users.

This improves loading speed and can provide additional security features.

## 7. Why should administrator accounts use MFA?

Administrator accounts have powerful permissions.

If an administrator password is stolen, an attacker could make significant changes to the system.

MFA provides an additional security layer.

## 8. Why should administrator access not be given to every employee?

Giving administrator access to every employee violates the Principle of Least Privilege.

It increases the risk of accidental changes, unauthorized access, and security incidents.

## 9. Why are logging and monitoring important?

Logging provides records of activities performed in the system.

Monitoring helps detect suspicious activities and potential security incidents.

Together, they help administrators investigate and respond to security problems.

## 10. Why are backups important?

Backups allow the organization to recover student information after accidental deletion, hardware failure, data corruption, or security incidents.

Regular backups help reduce the risk of permanent data loss.

---

# Final Architecture

The proposed secure architecture is:

Users
↓
CDN
↓
Load Balancer
↓
Application Server 1 / Application Server 2
↓
Private Database

The database is private and can only be accessed by authorized application servers.

The architecture uses IAM, MFA, firewalls/security groups, private subnets, encryption, logging, monitoring, and backups to improve security.
