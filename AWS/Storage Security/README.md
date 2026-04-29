# Security Fundamentals: Core Foundations - Storage Security

## Getting started
For setup instructions, please follow the steps provided in AWS.

### Storage Security
AWS provides multiple storage services (like Amazon S3, EBS, RDS, and Glacier) and each comes with built-in security features. The main pillars of storage security are encryption, access control, monitoring, and compliance.

##### 🗂️ Amazon S3 (Simple Storage Service)
- Provides scalable object storage with built-in security features like encryption and access control.
- Example: You create an S3 bucket for HR documents, enable Block Public Access, and enforce server-side encryption with KMS. Only HR IAM roles can access the bucket.

##### 💾 Amazon EBS (Elastic Block Store)
- Offers block-level storage volumes for EC2 instances with encryption and snapshot protection.
- Example: You attach an encrypted EBS volume to an EC2 instance running a payroll application. Snapshots are also encrypted automatically.

