# Security Fundamentals: Core Foundations - Data Security

## Getting started
For setup instructions, please follow the steps provided in Azure.

### Data Security
Azure ensures data security through a multilayered defense-in-depth approach, combining encryption, identity management, compliance certifications, and advanced threat protection to safeguard data at rest, in transit, and during processing. It follows Microsoft’s Zero Trust model, meaning every access request is verified, and data is protected across all stages.

##### 🔐 Azure SQL Database Security
- Advanced Data Security (ADS)
  - Provides vulnerability assessments, advanced threat protection, and data discovery/classification.
- Always Encrypted
  - Ensures sensitive data (like credit card numbers or SSNs) is encrypted both at rest and in use. Even administrators cannot access plaintext values.
- Encryption at Rest & In Transit
  - AES-256 secures stored data; TLS protects connections.
- Example: A healthcare provider stores patient records in Azure SQL. Doctors can query encrypted data, but administrators cannot view medical history in plaintext.

##### 🌍 Azure Cosmos DB Security
- Encryption at Rest
  - All data is automatically encrypted using AES-256.
- Role-Based Access Control (RBAC)
  - Fine-grained access control for users and applications.
- Network Security
  - Private endpoints and firewall rules restrict access.
- Example: An e-commerce app stores shopping carts in Cosmos DB. Even if accessed improperly, encryption prevents exposure of customer data.

##### 📊 Azure Data Lake Store Security
- Encryption at Rest & In Transit
  - AES-256 and TLS secure stored and transmitted data.
- Access Control Lists (ACLs)
  - Granular permissions at file and folder levels.
- Azure AD Integration
  - Centralized identity management.
- Example: A bank stores transaction logs in Data Lake. Analysts only access relevant folders, while encryption secures logs outside the environment.

##### 🧠 Azure HDInsight Security
- Encryption at Rest & In Transit
  - Protects big data clusters.
- Kerberos Authentication
  - Provides secure identity verification.
- Virtual Network Integration
  - Isolates clusters from public internet.
- Example: A telecom company analyzes call records with Hadoop jobs. Kerberos ensures only authorized analysts can run queries.

##### 🔑 Azure Key Vault
- Centralized Key Management
  - Stores encryption keys, secrets, and certificates.
- Hardware Security Modules (HSMs)
  - Keys are protected in FIPS 140-2 Level 2 validated HSMs.
- Access Policies
  - Define who can access or manage keys.
- Example: A fintech app stores API keys in Key Vault. Applications securely retrieve them at runtime, avoiding hardcoded secrets.

##### 📦 Azure Storage Security (Blob, Files, Queues, Tables)
- Encryption at Rest
  - Automatic AES-256 encryption for all storage types.
- Shared Access Signatures (SAS)
  - Fine-grained access tokens for temporary or limited access.
- Example: A media company stores video files in Blob Storage. SAS tokens allow temporary access without exposing account keys.

##### 🛡️ Azure Backup & Recovery
- Automated Backups 
  Protects against accidental deletion or corruption.
- Geo-Redundant Storage (GRS)
  Ensures data availability across regions.
- Example: A manufacturing company uses Azure Backup to protect ERP databases, ensuring recovery in case of ransomware attacks.

##### 🔒 Azure Confidential Computing
- Data-in-Use Protection
  Uses secure enclaves to protect data while being processed.
- Trusted Execution Environments (TEEs)
  Prevents unauthorized access even from cloud operators.
- Example: A financial institution runs risk models in confidential computing enclaves, ensuring sensitive data remains protected during analysis.
