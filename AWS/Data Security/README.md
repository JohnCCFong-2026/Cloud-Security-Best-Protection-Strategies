# Security Fundamentals: Core Foundations - Data Security

## Getting started
For setup instructions, please follow the steps provided in AWS.

### Data Security
AWS data security focuses on protecting information across its lifecycle at rest, in transit, and in use through layered safeguards. Core measures include encryption with hardware acceleration, secure communication protocols, isolated compute environments, identity and access controls, and continuous monitoring.

##### 🔑 AWS Key Management Service (KMS)
- Provides centralized control of encryption keys for securing data across AWS services.
- Example: Encrypting an Amazon RDS database with a KMS-managed key ensures sensitive financial records remain secure even if the physical storage is compromised.

##### 👥 AWS Identity and Access Management (IAM)
- Enables fine-grained access control to AWS resources, enforcing least privilege.
- Example: Restricting access so only specific IAM roles can read or write to sensitive S3 buckets.

##### 📦 Amazon S3 Security
- Offers bucket policies, Block Public Access, and server-side encryption with KMS integration.
- Example: Storing medical images in S3 with server-side encryption enabled and blocking all public access to prevent accidental exposure.

##### 🕵️ Amazon Macie
- Uses machine learning to discover and classify sensitive data such as PII in S3.
- Example: Automatically identifying credit card numbers stored in S3 and applying stricter access policies.

### Recommendations for AWS Data Security
##### 🛡️ AWS Backup & Recovery
- Provides automated backups to protect against accidental deletion or corruption.
- Supports cross-region replication for resilience and disaster recovery.
- Example: A manufacturing company uses AWS Backup to protect ERP databases, ensuring recovery in case of ransomware attacks.

##### AWS Nitro Enclaves
- Isolates sensitive workloads in secure enclaves.
- Protects data during processing, not just at rest or in transit.
- Example: A fintech company runs risk models in Nitro Enclaves, ensuring sensitive customer data remains secure during computation.

### Data Security Framework
##### Data Classification
- Categorize your data based on sensitivity and business impact (e.g., Public, Confidential, Secret) so you can apply the appropriate level of control.Protecting 

##### Data at Rest
- Ensure sensitive data is encrypted. Implement automated default encryption for data storage layers like Amazon S3 and Amazon EBS.Protecting 

##### Data in Transit
- Prevent data interception. Enforce TLS for all application traffic and API calls, and rely on secure key and certificate management.

##### AWS defense-in-depth model
-  Apply a layered approach that combines encryption, identity and access management, monitoring, automation, and resilience to safeguard data across its lifecycle.
