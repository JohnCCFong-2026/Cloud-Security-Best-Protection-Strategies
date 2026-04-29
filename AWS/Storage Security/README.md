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

##### 🗄️ Amazon RDS (Relational Database Service)
- Provides managed relational databases with encryption, network isolation, and automated backups.
- Example: You deploy a MySQL database in RDS, encrypt it with a KMS key, and restrict access to only application servers inside a private VPC.

##### 📚 Amazon S3 Glacier (Archival Storage)
- Long-term archival storage with compliance features like Vault Lock and encryption.
- Example: You archive medical records in Glacier with Vault Lock, ensuring they cannot be modified, meeting regulatory requirements.

##### 🔑 AWS Key Management Service (KMS)
- Centralized service for managing encryption keys across AWS storage services.
- Example: You use a customer-managed KMS key to encrypt both S3 objects and RDS databases, ensuring consistent encryption policies.

### Recommendations for AWS Storage Security
