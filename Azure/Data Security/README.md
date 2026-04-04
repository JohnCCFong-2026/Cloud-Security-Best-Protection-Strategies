# Security Fundamentals: Core Foundations - Data Security

## Getting started
For setup instructions, please follow the steps provided in Azure.

### Data Security
Azure ensures data security through a multilayered defense-in-depth approach, combining encryption, identity management, compliance certifications, and advanced threat protection to safeguard data at rest, in transit, and during processing. It follows Microsoft’s Zero Trust model, meaning every access request is verified, and data is protected across all stages.

##### 🔐 Azure SQL Database Security
- Always Encrypted
  - Ensures sensitive data (like credit card numbers or SSNs) is encrypted both at rest and in use. Even administrators cannot access plaintext values.
  - [Create, change, or delete a network security group](https://learn.microsoft.com/en-us/sql/relational-databases/security/encryption/always-encrypted-tutorial-getting-started?view=sql-server-ver17&viewFallbackFrom=azuresql&tabs=ssms)
- Transparent Data Encryption (TDE)
  - Encrypts the entire database, backups, and transaction logs automatically.
  - [Transparent data encryption for SQL Database, SQL Managed Instance, and Azure Synapse Analytics](https://learn.microsoft.com/en-us/azure/azure-sql/database/transparent-data-encryption-tde-overview?view=azuresql&tabs=azure-portal)
- Dynamic Data Masking (DDM)
  - Masks sensitive data in query results without altering the actual data.
  - [Dynamic data masking](https://learn.microsoft.com/en-us/azure/azure-sql/database/dynamic-data-masking-overview?view=azuresql)
- Encryption at Rest & In Transit
  - AES-256 secures stored data; TLS protects connections.
  - [An overview of Azure SQL Database and SQL Managed Instance security capabilities](https://learn.microsoft.com/en-us/azure/azure-sql/database/security-overview?view=azuresql)
- Example: A healthcare provider stores patient records in Azure SQL. Doctors can query encrypted data, but administrators cannot view medical history in plaintext.

##### 🌍 Azure Cosmos DB Security
- Encryption at Rest
  - All data is automatically encrypted using AES-256.
  - [https://learn.microsoft.com/en-us/azure/cosmos-db/database-encryption-at-rest](https://learn.microsoft.com/en-us/azure/cosmos-db/database-encryption-at-rest)
- Role-Based Access Control (RBAC)
  - Fine-grained access control for users and applications.
  - [Configure role-based access control in Azure Cosmos DB for MongoDB](https://learn.microsoft.com/en-us/azure/cosmos-db/mongodb/how-to-setup-role-based-access-control?tabs=python)
- Example: An e-commerce app stores shopping carts in Cosmos DB. Even if accessed improperly, encryption prevents exposure of customer data.

##### 📊 Azure Data Lake Storage Security
- Encryption at Rest & In Transit
  - AES-256 and TLS secure stored and transmitted data.
- Access Control Lists (ACLs)
  - Granular permissions at file and folder levels.
  - [Access control lists (ACLs) in Azure Data Lake Storage](https://learn.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-access-control)
- Azure AD Integration
  - Centralized identity management.
- Example: A bank stores transaction logs in Data Lake. Analysts only access relevant folders, while encryption secures logs outside the environment.

##### 🧠 Azure HDInsight Security
- Encryption at Rest & In Transit
  - Protects big data clusters.
  - [IPsec Encryption in transit for Azure HDInsight](https://learn.microsoft.com/sk-sk/%20azure/hdinsight/domain-joined/encryption-in-transit)
- Kerberos Authentication
  - Provides secure identity verification.
  - [Configure HDInsight clusters for Microsoft Entra integration with Enterprise Security Package](https://learn.microsoft.com/en-us/azure/hdinsight/domain-joined/apache-domain-joined-configure-using-azure-adds)
  - [Azure HDInsight architecture with Enterprise Security Package](https://github.com/MicrosoftDocs/azure-docs/blob/main/articles/hdinsight/domain-joined/apache-domain-joined-architecture.md) by kmurphy1000
- Example: A telecom company analyzes call records with Hadoop jobs. Kerberos ensures only authorized analysts can run queries.

##### 📦 Azure Storage Security (Blob, Files, Queues, Tables)
- Encryption at Rest
  - Automatic AES-256 encryption for all storage types.
  - [Azure Storage encryption for data at rest](https://learn.microsoft.com/en-us/azure/storage/common/storage-service-encryption)
- Shared Access Signatures (SAS)
  - Fine-grained access tokens for temporary or limited access.
  - [Grant limited access to Azure Storage resources using shared access signatures (SAS)](https://learn.microsoft.com/en-us/azure/storage/common/storage-sas-overview)
- Example: A media company stores video files in Blob Storage. SAS tokens allow temporary access without exposing account keys.

##### 🔑 Azure Key Vault
- Centralized Key Management
  - Stores encryption keys, secrets, and certificates.
  - [Create a key vault using the Azure portal](https://learn.microsoft.com/en-us/azure/key-vault/general/quick-create-portal)
- Hardware Security Modules (HSMs)
  - Keys are protected in FIPS 140-2 Level 2 validated HSMs.
  - [Provision and activate a Managed HSM using Azure CLI](https://learn.microsoft.com/en-us/azure/key-vault/managed-hsm/quick-create-cli)
- Azure role-based access control (Azure RBAC)
  - Define who can access or manage keys.
  - [Azure role-based access control (Azure RBAC) vs. access policies (legacy)](https://learn.microsoft.com/en-us/azure/key-vault/general/rbac-access-policy)
- Example: A fintech app stores API keys in Key Vault. Applications securely retrieve them at runtime, avoiding hardcoded secrets.

### Recommendations for Azure Data Security
##### 🛡️ Azure Backup & Recovery
- Automated Backups 
  - Protects against accidental deletion or corruption.
  - [Overview of security features in Azure Backup](https://learn.microsoft.com/en-us/azure/backup/security-overview)
- Geo-Redundant Storage (GRS)
  Ensures data availability across regions.
- Example: A manufacturing company uses Azure Backup to protect ERP databases, ensuring recovery in case of ransomware attacks.

##### 🛡️ Microsoft Defender for SQL (pricing required)
- A unified security package that provides vulnerability assessments, advanced threat protection, and data discovery/classification.
- Explore Microsoft Defender for SQL capabilities
- [Microsoft Defender for SQL](https://learn.microsoft.com/en-us/azure/azure-sql/database/azure-defender-for-sql?view=azuresql)

##### 🔒 Azure Confidential Computing
- Data-in-Use Protection
  - Uses secure enclaves to protect data while being processed.
  - [Protecting data privacy and security on your most sensitive workloads](https://azure.microsoft.com/en-us/solutions/confidential-compute)
- Trusted Execution Environments (TEEs)
  - Prevents unauthorized access even from cloud operators.
  - [Trusted Execution Environment (TEE)](https://learn.microsoft.com/en-us/azure/confidential-computing/trusted-execution-environment)
- Example: A financial institution runs risk models in confidential computing enclaves, ensuring sensitive data remains protected during analysis.

### Data Security Framework
##### Microsoft Purview (Data Loss Prevention (DLP)) (pricing required)
- Prevents sensitive data from being leaked or misused by monitoring and controlling data movement.
- Example: Configure policies to block credit card numbers from being copied out of VMs or uploaded to unauthorized storage.
- [Learn about the information protection scanner](https://learn.microsoft.com/en-us/purview/deploy-scanner#learn-about-the-information-protection-scanner)
