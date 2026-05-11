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

### Data Security Framework
##### 🔑 Encryption at Rest
- AWS protects stored data using AWS Key Management Service (KMS) integrated with services like Amazon S3, Amazon RDS, and Amazon EBS.
- Encryption is automatic when enabled, and keys are centrally managed in KMS.
- Example: Encrypting an EBS volume with a KMS-managed key ensures that even if the physical disk is compromised, the data remains unreadable without the decryption key.

##### 🌐 Encryption in Transit
- Data moving between clients, applications, and AWS services is secured using TLS/SSL protocols.
- AWS also provides AWS Certificate Manager (ACM) to simplify provisioning and managing SSL/TLS certificates for secure communication.
- Example: Enforcing HTTPS for all public endpoints ensures secure communication between users and applications, preventing eavesdropping or tampering.

##### ⚙️ Encryption in Use (Compute)
- AWS protects data while it is actively being processed in memory or inside compute environments.
- This is achieved through AWS Nitro Enclaves and confidential computing, which isolate sensitive workloads from the host OS and other applications.
- Example: Running workloads in Nitro Enclaves ensures sensitive data (like medical records or financial transactions) is processed securely, and even system administrators cannot access plaintext values during computation.
