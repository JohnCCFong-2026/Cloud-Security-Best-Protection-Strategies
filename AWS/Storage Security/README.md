# Security Fundamentals: Core Foundations - Storage Security

## Getting started
For setup instructions, please follow the steps provided in AWS.

### Storage Security
AWS provides multiple storage services (like Amazon S3, EBS, RDS, and Glacier) and each comes with built-in security features. The main pillars of storage security are encryption, access control, monitoring, and compliance.

##### 💾 Amazon EBS (Elastic Block Store)
- Offers block-level storage volumes for EC2 instances with encryption and snapshot protection.
- Example: You attach an encrypted EBS volume to an EC2 instance running a payroll application. Snapshots are also encrypted automatically.
- [Security in Amazon EBS](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.html)

##### 🗄️ Amazon RDS (Relational Database Service)
- Provides managed relational databases with encryption, network isolation, and automated backups.
- Example: You deploy a MySQL database in RDS, encrypt it with a KMS key, and restrict access to only application servers inside a private VPC.
- [Security in Amazon RDS](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.html)

##### 🗂️ Amazon S3 (Simple Storage Service)
- Provides scalable object storage with built-in security features like encryption and access control.
- Example: You create an S3 bucket for HR documents, enable Block Public Access, and enforce server-side encryption with KMS. Only HR IAM roles can access the bucket.
- [Security in Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/security.html)

##### 📚 Amazon S3 Glacier (Archival Storage)
- Long-term archival storage with compliance features like Vault Lock and encryption.
- Example: You archive medical records in Glacier with Vault Lock, ensuring they cannot be modified, meeting regulatory requirements.
- [Locking a Vault using the AWS Command Line Interface](https://docs.aws.amazon.com/amazonglacier/latest/dev/vault-lock-how-to-cli.html)

##### 🔑 S3 Pre-signed URLs
- A secure method to grant temporary, limited access to a specific S3 object without requiring the recipient to have AWS credentials.
- Example: You generate a link for a client to download a specific report. You set the link to expire in 30 minutes. Once the time is up, the link automatically becomes invalid.
- [Sharing objects with presigned URLs](https://docs.aws.amazon.com/AmazonS3/latest/userguide/ShareObjectPreSignedURL.html)

##### 🔐 S3 Block Public Access (The Safety Net)
- A global setting that acts as a master fail-safe to prevent any S3 bucket from being made public, even if a user makes a mistake in a policy.
- Best Practice: Enable this at the Account Level immediately.
- Example: A junior admin accidentally sets a bucket policy to "Public." Because Block Public Access is on at the account level, the bucket stays private, preventing a data leak.
- [Blocking public access to your Amazon S3 storage](https://docs.aws.amazon.com/AmazonS3/latest/userguide/access-control-block-public-access.html)

##### 🔑 AWS Key Management Service (KMS)
- Centralized service for managing encryption keys across AWS storage services.
- Example: You use a customer-managed KMS key to encrypt both S3 objects and RDS databases, ensuring consistent encryption policies.
- [Data protection in AWS Key Management Service](https://docs.aws.amazon.com/kms/latest/developerguide/data-protection.html)

##### 📂 Amazon EFS (Elastic File System)
- Provides serverless, fully managed file shares for Linux-based workloads via the NFS protocol.
- Example: You use EFS to provide shared storage for a fleet of web servers. Access is controlled by Security Groups at the network level and POSIX permissions at the file level.
- [Securing your data in Amazon EFS](https://docs.aws.amazon.com/efs/latest/ug/security-considerations.html)

##### 🛡️ VPC Endpoints 
- A private connection between your Virtual Private Cloud (VPC) and AWS services (like S3 or DynamoDB). It ensures your data travels over the AWS private network rather than the public internet.
- Example: You have a backend server in a private subnet with no internet access. By creating an S3 Gateway Endpoint, that server can securely upload logs to an S3 bucket without needing a NAT Gateway or an internet connection.
- [Control access to VPC endpoints using endpoint policies](https://docs.aws.amazon.com/vpc/latest/privatelink/vpc-endpoints-access.html)

##### 🛡️ VPC Security Groups & Network ACLs
- Acts as a virtual firewall to control inbound and outbound traffic for storage-related resources like RDS databases or EFS file systems. Security Groups are stateful (track connections), while Network ACLs are stateless (act at the subnet level).
- Example: You deploy a PostgreSQL database in RDS. You attach a Security Group that only allows incoming traffic on port 5432 from the specific Security Group ID belonging to your web servers, blocking all other attempts to connect to the database.
- [Security groups and network ACLs (BP5)](https://docs.aws.amazon.com/whitepapers/latest/aws-best-practices-ddos-resiliency/security-groups-and-network-acls-bp5.html)

### Recommendations for AWS Storage Security
##### 🏷️ Amazon Macie (Sensitive Data Discovery)
- Automatically discovers and protects sensitive data (like PII, credit card numbers, or API keys) stored in Amazon S3.
- Even with perfect encryption, you may accidentally store sensitive data in the wrong bucket. Macie uses machine learning to alert you to these data privacy risks.
- Example: You run a Macie scan on a legacy S3 bucket and find unencrypted CSV files containing customer social security numbers. You immediately move them to a restricted vault.
- [Monitoring data security and privacy with Macie](https://docs.aws.amazon.com/macie/latest/user/monitoring-s3.html)

##### 🔄 AWS Backup (Centralized Governance)
- A fully managed service to centralize and automate data protection across AWS services (EBS, RDS, EFS, and S3).
- It prevents "backup silos" by allowing you to manage retention policies and disaster recovery in one place.
- Example: You create a single Backup Plan that automatically backs up your RDS databases every 24 hours and copies them to a different AWS Region for disaster recovery.
- [Security in AWS Backup](https://docs.aws.amazon.com/aws-backup/latest/devguide/security-considerations.html)

### Storage Security Framework
##### Least Privilege Access
- Use IAM roles and policies to grant only the permissions needed.
- Enforce MFA for sensitive operations.
- Rotate and audit credentials regularly.
- Example: An application role can only read from one S3 bucket, not write or access others.

##### Data Protection
- Encrypt data at rest with AWS KMS (customer‑managed or AWS‑managed keys).
- Encrypt data in transit using TLS/SSL.
- Use automatic encryption features (EBS Nitro, RDS managed encryption).
- Example: RDS databases encrypted with a customer‑managed KMS key.

##### Infrastructure Protection
- Use VPC Endpoints for private connectivity to S3/DynamoDB.
- Configure Security Groups & Network ACLs to control inbound/outbound traffic.
- Isolate sensitive workloads with Nitro Enclaves.
- Example: Logs uploaded securely from a private subnet to S3 via a Gateway Endpoint.

##### Detection & Monitoring
- Enable AWS CloudTrail to log all storage API calls.
- Use Amazon Macie to discover and classify sensitive data in S3.
- Monitor with Amazon GuardDuty for suspicious activity.
- Centralize logs with AWS Security Lake.
- Example: Macie alerts you to unencrypted CSV files with PII in a legacy bucket.

##### Incident Response
- Automate alerts for unusual access patterns.
- Use immutable backups with Glacier Vault Lock.
- Implement AWS Backup for centralized disaster recovery.
- Example: Daily RDS backups copied to another region for DR readiness.

##### Compliance & Governance
- Enforce Block Public Access globally for S3.
- Use AWS Config for compliance auditing.
- Apply data residency controls to meet regulatory requirements.
- Example: Prevent accidental public exposure of S3 buckets at the account level.
