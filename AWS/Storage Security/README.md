# Security Fundamentals: Core Foundations - Storage Security

## Getting started
For setup instructions, please follow the steps provided in AWS.

### Storage Security
AWS provides multiple storage services (like Amazon S3, EBS, RDS, and Glacier) and each comes with built-in security features. The main pillars of storage security are encryption, access control, monitoring, and compliance.

##### 🗂️ Amazon S3 (Simple Storage Service)
- Block Public Access (prevent accidental exposure).
- Bucket policies & ACLs for fine-grained access.
- Server-Side Encryption (SSE) with AWS KMS.
- Object Lock for immutability.
- Example: Store customer invoices in an encrypted S3 bucket, accessible only by the Finance IAM role.

