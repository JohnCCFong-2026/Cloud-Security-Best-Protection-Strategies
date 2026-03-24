# Security Fundamentals: Core Foundations - Storage Security

## Getting started
For setup instructions, please follow the steps provided in Azure.

### Storage Security
Azure ensures that data stored in the cloud is protected against unauthorized access, corruption, and loss. The goal is to safeguard sensitive information (files, databases, backups) while maintaining availability and compliance with industry standards.

##### 🔑 Shared Access Signatures (SAS)
- A secure method to grant temporary, limited access to Azure Storage resources—such as blobs, files, queues, or tables—without exposing the storage account key.
- [Shared access signature (SAS) tokens for storage containers](https://docs.azure.cn/en-us/ai-services/translator/document-translation/how-to-guides/create-sas-tokens?tabs=Containers)

##### 🛡️ Storage firewall
- A security feature that protects Azure data services (including Storage, SQL Database, Cosmos DB, and more) by restricting access based on networks, IP addresses, or Azure resources. It acts as a gatekeeper, ensuring only trusted sources can connect to your storage account or database.
- [Azure Storage firewall rules](https://learn.microsoft.com/en-us/azure/storage/common/storage-network-security#:~:text=Azure%20Storage%20firewall%20rules%20control%20network%20access,storage%20account.%20All%20other%20traffic%20is%20denied.)

##### 🆔 Microsoft Entra ID integration
- Provides identity-based access control for Azure Storage and other services like Azure SQL Database, Azure Files, and Cosmos DB. Instead of relying on long-lived account keys or connection strings, you can enforce secure authentication and authorization through Entra ID.
- [Configure and manage Microsoft Entra authentication with Azure SQL](https://learn.microsoft.com/en-us/azure/azure-sql/database/authentication-aad-configure?view=azuresql&tabs=azure-portal)

##### 🔑 Customer-Managed Keys (CMK)
- Organizations have direct control over the encryption keys used to protect their data in Azure Storage by using Customer-Managed Keys (CMK). Instead of relying only on Microsoft-managed keys, you store and manage your own keys in Azure Key Vault, which ensures that you retain ultimate authority over encryption and decryption.
- [Configure customer-managed keys in the same tenant for a new storage account](https://docs.azure.cn/en-us/storage/common/customer-managed-keys-configure-new-account?tabs=azure-portal)

