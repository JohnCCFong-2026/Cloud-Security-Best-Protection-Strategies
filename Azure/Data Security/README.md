# Security Fundamentals: Core Foundations - Data Security

## Getting started
For setup instructions, please follow the steps provided in Azure.

### Data Security
Azure ensures data security through a multilayered defense-in-depth approach, combining encryption, identity management, compliance certifications, and advanced threat protection to safeguard data at rest, in transit, and during processing. It follows Microsoft’s Zero Trust model, meaning every access request is verified, and data is protected across all stages.

##### 🔐 Azure SQL Database Security
- Advanced Data Security (ADS)
  - Provides vulnerability assessments, advanced threat protection, and data discovery/classification.
- Always Encrypted
  - Ensures sensitive data (like credit card numbers or SSNs) is encrypted both at rest and in use. Even DB admins cannot see plaintext values.
- Encryption in Transit & Rest
  - TLS secures connections; AES-256 encrypts stored data.
- Example: A healthcare company stores patient records in Azure SQL. With Always Encrypted, doctors can query patient data, but the database administrator cannot read sensitive fields like medical history because they remain encrypted with client-side keys.

##### 🌍 Azure Cosmos DB Security
- Encryption at Rest
  - All data is automatically encrypted using AES-256.
- Role-Based Access Control (RBAC)
  - Fine-grained access control for users and apps.
- Network Security
  - Private endpoints and firewall rules restrict access.
- Example: An e-commerce app uses Cosmos DB to store customer shopping carts. Even if someone gains unauthorized access to the storage account, the data is unreadable without the encryption keys.

##### 📊 Azure Data Lake Store Security
- Encryption at Rest & In Transit
  - Data is encrypted using AES-256 and TLS.
- Access Control Lists (ACLs)
  - Granular permissions at file and folder levels.
- Integration with Azure AD
  - Centralized identity management.
- Example: A bank stores transaction logs in Data Lake. Analysts can access only the folders relevant to their department, while encryption ensures logs remain secure even if copied outside.

##### 🧠 Azure HDInsight Security
- Encryption at Rest & In Transit
  - Protects big data clusters.
- Kerberos Authentication
  - Provides secure identity verification.
- Integration with Azure Virtual Network
  - Isolates clusters from public internet.
- Example: A telecom company runs Hadoop jobs on HDInsight to analyze call records. Kerberos ensures only authorized analysts can run queries, while encryption keeps raw call data secure.

##### 🔑 Azure Key Vault
- Centralized Key Management
  - Stores encryption keys, secrets, and certificates.
- Hardware Security Modules (HSMs)
  - Keys are protected in FIPS 140-2 Level 2 validated HSMs.
- Access Policies
  - Define who can access or manage keys.
- Example: A fintech app uses Key Vault to store API keys and database connection strings. Developers never hardcode secrets in code; instead, applications fetch them securely at runtime.


