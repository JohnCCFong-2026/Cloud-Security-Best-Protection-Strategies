# Security Fundamentals: Core Foundations - Host Security

## Getting started
For setup instructions, please follow the steps provided in AWS.

### Host Security
AWS host security focuses on safeguarding the compute environment, including EC2 instances and workloads, through layered protections. Core measures include instance hardening, patch management, identity and access controls, encryption, monitoring, and intrusion detection.

##### 🛡️ Amazon EBS Encryption (Nitro System)
- Provides seamless, hardware-accelerated encryption for data at rest and in transit between the host and storage.
- Example: On Nitro-based instances, encryption is handled by dedicated hardware, ensuring there is zero impact on the CPU performance of your application while keeping your disks secure.

##### 🧠 AWS Nitro Enclaves
- Creates isolated compute environments to protect and process highly sensitive "data in use" (data in memory).
- Example: A healthcare app processes sensitive patient data inside a Nitro Enclave. This environment has no persistent storage or interactive access, ensuring even a "root" administrator cannot see the data being processed.
