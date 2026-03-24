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

