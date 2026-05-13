# Security Fundamentals: Core Foundations - Data Security

## Getting started
For setup instructions, please follow the steps provided in AWS.

### Data Security
AWS data security focuses on protecting information across its lifecycle at rest, in transit, and in use through layered safeguards. Core measures include encryption with hardware acceleration, secure communication protocols, isolated compute environments, identity and access controls, and continuous monitoring.

##### 🔑 AWS Key Management Service (KMS)
- Provides centralized control of encryption keys for securing data across AWS services.
- Example: Encrypting an Amazon RDS database with a KMS-managed key ensures sensitive financial records remain secure even if the physical storage is compromised.
- [Data protection in AWS Key Management Service](https://docs.aws.amazon.com/kms/latest/developerguide/data-protection.html)

##### 👥 AWS Identity and Access Management (IAM)
- Enables fine-grained access control to AWS resources, enforcing least privilege.
- Example: Restricting access so only specific IAM roles can read or write to sensitive S3 buckets.
- [Data protection in AWS Identity and Access Management](https://docs.aws.amazon.com/IAM/latest/UserGuide/data-protection.html)

##### 📦 Amazon S3 Security
- Offers bucket policies, Block Public Access, and server-side encryption with KMS integration.
- Example: Storing medical images in S3 with server-side encryption enabled and blocking all public access to prevent accidental exposure.
- [Using server-side encryption with AWS KMS keys (SSE-KMS)](https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingKMSEncryption.html)

##### 🕵️ Amazon Macie
- Uses machine learning to discover and classify sensitive data such as PII in S3.
- Example: Automatically identifying credit card numbers stored in S3 and applying stricter access policies.
- [Data protection in Macie](https://docs.aws.amazon.com/macie/latest/user/data-protection.html)

### Recommendations for AWS Data Security
##### 🛡️ AWS Backup & Recovery
- Provides automated backups to protect against accidental deletion or corruption.
- Supports cross-region replication for resilience and disaster recovery.
- Example: A manufacturing company uses AWS Backup to protect ERP databases, ensuring recovery in case of ransomware attacks.
- [Data protection in AWS Backup](https://docs.aws.amazon.com/aws-backup/latest/devguide/data-protection.html)

##### 🧠 AWS Nitro Enclaves
- Isolates sensitive workloads in secure enclaves.
- Protects data during processing, not just at rest or in transit.
- Example: A fintech company runs risk models in Nitro Enclaves, ensuring sensitive customer data remains secure during computation.

### Data Security Framework
##### 🔍 Data Classification
- Categorize data based on sensitivity and business impact (e.g., Public, Confidential, Secret).
- Ensures appropriate controls are applied to critical or regulated data.
- Example: Patient records classified as Secret require encryption and strict IAM policies.

##### 🔒 Data at Rest
- Encrypt sensitive data by default using AWS KMS and service‑level encryption (Amazon S3, Amazon EBS, Amazon RDS).
- Protects stored data from unauthorized access.
- Example: A bank encrypts transaction logs in Amazon S3 with KMS keys to meet compliance requirements.

##### 🔐 Data in Transit
- Prevent interception or tampering during transfer.
- Enforce TLS for all application traffic and API calls, and manage certificates securely with AWS Certificate Manager (ACM).
- Example: An e‑commerce app uses TLS to secure customer payment data transmitted between the web app and RDS.

##### 🧠 Data in Use
- Protect sensitive data while being processed in memory.
- AWS Nitro Enclaves isolate workloads, ensuring encrypted data remains secure during computation.
- Example: A fintech company runs risk models in Nitro Enclaves, keeping customer data protected even during analysis.

##### 🛡️ AWS defense-in-depth model
-  Apply a layered approach that combines classification, encryption at rest and in transit, encrypted safeguards for data in use, identity and access management, monitoring and detection (CloudTrail, GuardDuty, Macie), compliance automation (AWS Config), centralized security management (Security Hub), and resilience (AWS Backup).
- Ensures that no single point of failure can compromise sensitive information.
