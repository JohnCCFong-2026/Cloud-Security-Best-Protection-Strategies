# Security Fundamentals: Core Foundations - Storage Security

## Getting started
For setup instructions, please follow the steps provided in AWS.

### Storage Security
AWS provides multiple storage services (like Amazon S3, EBS, RDS, and Glacier) and each comes with built-in security features. The main pillars of storage security are encryption, access control, monitoring, and compliance.

##### 💾 Amazon EBS (Elastic Block Store)
- Offers block-level storage volumes for EC2 instances with encryption and snapshot protection.
- Example: You attach an encrypted EBS volume to an EC2 instance running a payroll application. Snapshots are also encrypted automatically.

##### 🗄️ Amazon RDS (Relational Database Service)
- Provides managed relational databases with encryption, network isolation, and automated backups.
- Example: You deploy a MySQL database in RDS, encrypt it with a KMS key, and restrict access to only application servers inside a private VPC.

##### 🗂️ Amazon S3 (Simple Storage Service)
- Provides scalable object storage with built-in security features like encryption and access control.
- Example: You create an S3 bucket for HR documents, enable Block Public Access, and enforce server-side encryption with KMS. Only HR IAM roles can access the bucket.

##### 📚 Amazon S3 Glacier (Archival Storage)
- Long-term archival storage with compliance features like Vault Lock and encryption.
- Example: You archive medical records in Glacier with Vault Lock, ensuring they cannot be modified, meeting regulatory requirements.

##### 🔑 S3 Pre-signed URLs
- A secure method to grant temporary, limited access to a specific S3 object without requiring the recipient to have AWS credentials.
- Example: You generate a link for a client to download a specific report. You set the link to expire in 30 minutes. Once the time is up, the link automatically becomes invalid.

##### 🔐 S3 Block Public Access (The Safety Net)
- A global setting that acts as a master fail-safe to prevent any S3 bucket from being made public, even if a user makes a mistake in a policy.
- Best Practice: Enable this at the Account Level immediately.
- Example: A junior admin accidentally sets a bucket policy to "Public." Because Block Public Access is on at the account level, the bucket stays private, preventing a data leak.

##### 🔑 AWS Key Management Service (KMS)
- Centralized service for managing encryption keys across AWS storage services.
- Example: You use a customer-managed KMS key to encrypt both S3 objects and RDS databases, ensuring consistent encryption policies.

##### 📂 Amazon EFS (Elastic File System)
- Provides serverless, fully managed file shares for Linux-based workloads via the NFS protocol.
- Example: You use EFS to provide shared storage for a fleet of web servers. Access is controlled by Security Groups at the network level and POSIX permissions at the file level.

##### 🛡️ Amazon EBS Encryption (Nitro System)
- Provides seamless, hardware-accelerated encryption for data at rest and in transit between the host and storage.
- Example: On Nitro-based instances, encryption is handled by dedicated hardware, ensuring there is zero impact on the CPU performance of your application while keeping your disks secure.

##### 🧠 AWS Nitro Enclaves
- Creates isolated compute environments to protect and process highly sensitive "data in use" (data in memory).
- Example: A healthcare app processes sensitive patient data inside a Nitro Enclave. This environment has no persistent storage or interactive access, ensuring even a "root" administrator cannot see the data being processed.

##### 🛡️ VPC Endpoints 
- A private connection between your Virtual Private Cloud (VPC) and AWS services (like S3 or DynamoDB). It ensures your data travels over the AWS private network rather than the public internet.
- Example: You have a backend server in a private subnet with no internet access. By creating an S3 Gateway Endpoint, that server can securely upload logs to an S3 bucket without needing a NAT Gateway or an internet connection.

##### 🛡️ VPC Security Groups & Network ACLs
- Acts as a virtual firewall to control inbound and outbound traffic for storage-related resources like RDS databases or EFS file systems. Security Groups are stateful (track connections), while Network ACLs are stateless (act at the subnet level).
- Example: You deploy a PostgreSQL database in RDS. You attach a Security Group that only allows incoming traffic on port 5432 from the specific Security Group ID belonging to your web servers, blocking all other attempts to connect to the database.

### Recommendations for AWS Storage Security
##### 🏷️ Amazon Macie (Sensitive Data Discovery)
- Automatically discovers and protects sensitive data (like PII, credit card numbers, or API keys) stored in Amazon S3.
- Even with perfect encryption, you may accidentally store sensitive data in the wrong bucket. Macie uses machine learning to alert you to these data privacy risks.
- Example: You run a Macie scan on a legacy S3 bucket and find unencrypted CSV files containing customer social security numbers. You immediately move them to a restricted vault.

##### 🔄 AWS Backup (Centralized Governance)
- A fully managed service to centralize and automate data protection across AWS services (EBS, RDS, EFS, and S3).
- It prevents "backup silos" by allowing you to manage retention policies and disaster recovery in one place.
- Example: You create a single Backup Plan that automatically backs up your RDS databases every 24 hours and copies them to a different AWS Region for disaster recovery.
