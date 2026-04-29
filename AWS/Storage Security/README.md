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

##### 📂 Azure Files (Cloud File Shares)
- Provides fully managed file shares accessible via SMB or NFS, supporting standard NTFS permissions.
- Integrates with Active Directory Domain Services (AD DS) to allow users to use their corporate credentials for access.
- Example: You migrate an on-premises file server to Azure Files, maintaining the same folder-level permissions (ACLs) for your employees.

##### 🛡️ Encryption at Host
- Provides end-to-end encryption by encrypting data at the VM host before it is written to storage.
- Unlike the retiring Azure Disk Encryption (ADE), this handles temporary disks and caches without OS-level overhead.
- Example: You enable Encryption at Host for a high-performance database VM to ensure the cache and data disks are encrypted before they even leave the host server.

##### 🧠 Confidential Computing
- Protects "data in use" by performing computations in a hardware-based Trusted Execution Environment (TEE).
- Example: A healthcare app processes patient records in a Confidential VM, ensuring even Azure administrators cannot see the data in memory.

##### S3 Pre-signed URLs
- A secure method to grant temporary, limited access to a specific S3 object without requiring the recipient to have AWS credentials. You define exactly how long the link remains valid (e.g., 15 minutes).
- Example: You need to share a private 2GB video file with an external contractor. Instead of making the bucket public, you generate a pre-signed URL that expires in 1 hour. The contractor downloads the file via that specific link, which becomes useless immediately after the hour passes.

##### VPC Endpoints 
- A private connection between your Virtual Private Cloud (VPC) and AWS services (like S3 or DynamoDB). It ensures your data travels over the AWS private network rather than the public internet.
- Example: You have a backend server in a private subnet with no internet access. By creating an S3 Gateway Endpoint, that server can securely upload logs to an S3 bucket without needing a NAT Gateway or an internet connection.

##### 🛡️ VPC Security Groups & Network ACLs
- Acts as a virtual firewall to control inbound and outbound traffic for storage-related resources like RDS databases or EFS file systems. Security Groups are stateful (track connections), while Network ACLs are stateless (act at the subnet level).
- Example: You deploy a PostgreSQL database in RDS. You attach a Security Group that only allows incoming traffic on port 5432 from the specific Security Group ID belonging to your web servers, blocking all other attempts to connect to the database.

### Recommendations for AWS Storage Security
