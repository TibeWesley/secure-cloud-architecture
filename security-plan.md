```markdown
# Secure Cloud Architecture Plan

## Introduction

This project shows a simple and secure cloud architecture for a Student Management Application.

The application allows users to view student information. The main goal is to keep the system easy to use while also protecting student information from unauthorized access.

The proposed architecture is:

Users
↓
CDN
↓
Load Balancer
↓
Application Servers
↓
Private Database

---

# Cloud Architecture Components

## CDN

CDN stands for Content Delivery Network.

The CDN helps deliver website files, such as HTML, CSS, and images, faster to users. It keeps copies of these files in different locations so users can get them from a location that is closer to them.

The CDN can be accessed from the Internet.

## Load Balancer

The load balancer receives requests from users and sends them to the available application servers.

For example, if there are two application servers, the load balancer can send some users to Server 1 and other users to Server 2.

This prevents one server from doing all the work.

## Application Servers

The application servers handle the main work of the Student Management Application.

They receive requests from the load balancer, process the request, and communicate with the database when information is needed.

The application servers should be placed in a private subnet so they are not directly exposed to the Internet.

## Database

The database stores important student information such as student numbers, names, courses, year levels, and email addresses.

The database should remain private.

It should only accept connections from the application servers and should not be directly accessible from the Internet.

---

# Public and Private Resources

| Resource | Public or Private? | Explanation |
|---|---|---|
| CDN | Public | The CDN needs to deliver website content to users through the Internet. |
| Load Balancer | Public | Users need to connect to the load balancer to access the application. |
| Application Server | Private | Application servers should not be directly accessible from the Internet. |
| Database | Private | The database contains student information and should only be accessed by the application servers. |

---

# Security Controls

## IAM

IAM stands for Identity and Access Management.

IAM controls who can access the cloud environment and what they are allowed to do.

Only authorized employees should have access to the cloud resources. Each person should only receive the permissions they need to do their job.

For example, an administrator may manage the whole system, while an instructor may only access student records.

## MFA

MFA stands for Multi-Factor Authentication.

MFA provides an additional layer of security when logging in.

Administrator accounts should always use MFA because they have access to important system settings and resources.

Even if an administrator's password is stolen, MFA can help prevent an attacker from logging in.

## Firewall / Security Group

The firewall or security groups control which connections are allowed.

The basic rules are:

- Internet → Load Balancer = Allowed
- Load Balancer → Application Server = Allowed
- Application Server → Database = Allowed
- Internet → Application Server = Blocked
- Internet → Database = Blocked

These rules help prevent unauthorized people from directly accessing private resources.

## Encryption

Student information should be encrypted to protect it from unauthorized people.

Encryption changes information into a form that cannot easily be understood without the correct key.

Data should be protected both when it is being sent over the network and when it is stored.

## Logging

Logging keeps a record of important activities in the system.

Examples of activities that can be recorded include:

- User logins
- Failed login attempts
- Changes to user permissions
- Database access
- Changes to application settings
- Security-related events

Logs can help administrators understand what happened when there is a problem.

## Monitoring

Monitoring helps administrators watch the system for unusual or suspicious activity.

Examples include:

- Many failed login attempts
- Unusual traffic
- Unexpected changes to resources
- High server usage
- Unauthorized access attempts

Monitoring can help detect security problems early.

## Backup

The database should have regular backups.

Backups provide another copy of the student information if the original database is accidentally deleted, damaged, or affected by a security problem.

Having backups makes it easier to restore the system and prevent permanent data loss.

---

# Principle of Least Privilege

The Principle of Least Privilege means that users should only receive the access they need to perform their job.

| User | Allowed Access |
|---|---|
| Administrator | Manage users, security settings, application resources, and database settings. |
| Instructor | View and manage student information needed for teaching. |
| Student | View their own student information. |
| Developer | Access application code and development resources but should not have unnecessary access to student data or administrator settings. |

Not everyone should have administrator access.

Giving too many permissions can increase the chance of accidental changes or unauthorized access.

---

# Shared Responsibility Model

Cloud security is shared between the cloud provider and the customer.

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

## 1. What does Security OF the Cloud mean?

Security OF the Cloud means protecting the physical cloud infrastructure.

The cloud provider is responsible for things such as physical data centers, physical servers, networking equipment, and the basic infrastructure used to provide the cloud service.

## 2. What does Security IN the Cloud mean?

Security IN the Cloud means protecting the resources and information that the customer puts into the cloud.

The customer is responsible for things such as user accounts, passwords, IAM permissions, application security, student data, database access rules, and backups.

---

# Architecture Questions

## 3. Which resource should be directly accessible from the Internet?

The load balancer should be directly accessible from the Internet.

Users connect to the load balancer, and the load balancer sends their requests to the application servers.

The database should not be directly accessible from the Internet.

## 4. Why should the database remain private?

The database contains important student information.

Keeping it private reduces the chance of unauthorized people accessing or stealing the information.

## 5. Why should users not connect directly to the database?

Users should not connect directly to the database because this could expose sensitive information and database services to attackers.

Instead, users should communicate with the application, and the application communicates with the database.

## 6. What is the purpose of a load balancer?

The load balancer distributes user requests between application servers.

This helps prevent one server from becoming overloaded.

## 7. What happens if one application server fails?

If one application server fails, the load balancer can send users to another working application server.

This helps keep the application available.

## 8. What is the purpose of a CDN?

The CDN helps deliver website content faster.

It stores copies of static website content in different locations so users can receive the content from a location closer to them.

## 9. Why should administrator accounts use MFA?

Administrator accounts have more power and can make important changes to the system.

MFA adds another security check and makes it harder for someone to access the account using only a stolen password.

## 10. Why should administrator access not be given to every employee?

Giving administrator access to everyone creates unnecessary security risks.

Employees should only receive the permissions needed for their work.

## 11. Why are logging and monitoring important?

Logging and monitoring help administrators see what is happening in the system.

They can help identify unusual activity, security problems, failed login attempts, and unauthorized access.

## 12. Why are backups important?

Backups provide another copy of important information.

If the database is accidentally deleted, damaged, or affected by a security incident, the backup can be used to restore the information.

---

# Conclusion

The proposed architecture uses a CDN, load balancer, application servers, and a private database.

The public-facing part of the system allows users to access the application, while the application servers and database are kept private.

Security controls such as IAM, MFA, firewalls, encryption, logging, monitoring, and backups help protect the application and student information.

This design follows the principle of least privilege and the Shared Responsibility Model.

The goal is to provide users with access to the application while keeping important resources and student information protected.
```
