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
- Organizations can directly control the encryption keys used to protect their data in Azure Storage by using Customer-Managed Keys (CMK). These keys are stored and managed in Azure Key Vault, ensuring that customers retain ultimate authority over encryption and decryption.
- [Configure customer-managed keys in the same tenant for a new storage account](https://docs.azure.cn/en-us/storage/common/customer-managed-keys-configure-new-account?tabs=azure-portal)

##### 🛣️ Private Endpoint
- A Private Endpoint in Azure is a network interface that securely connects you to Azure services using a private IP address from your Virtual Network (VNet). This ensures traffic between your VNet and the Azure service travels entirely over the Microsoft backbone network, rather than the public internet.
- Private Endpoints are part of **Azure Private Link** and can be used with services such as **Azure Storage**, **Azure SQL Database**, **Cosmos DB**, and **Key Vault**.
- They help prevent **data exfiltration risks** by keeping traffic within Azure’s trusted network.
- Private Endpoints integrate with **Resource Firewalls** and **Private DNS zones** to provide fine-grained, secure, and seamless access to resources.
- [Create a private endpoint by using the Azure portal](https://learn.microsoft.com/en-us/azure/private-link/create-private-endpoint-portal?tabs=dynamic-ip)

### Recommendations for Azure Storage Security
##### 🔐 Encryption at Rest
- Protects data when it is stored on disk in Azure Storage. By default, Azure automatically encrypts all data at rest using AES-256 with Microsoft-managed keys. You can optionally use Customer-Managed Keys (CMK) in Azure Key Vault for more control.
- Example: You upload a backup file to Blob Storage. Azure encrypts it before writing it to disk. Even if someone accessed the physical storage, they would only see encrypted data, not the original file.
- [Azure data encryption at rest](https://learn.microsoft.com/en-us/azure/security/fundamentals/encryption-atrest)

##### 🔐 Encryption at Transit
- Protects data while it is moving between your client and Azure Storage. Azure supports HTTPS/TLS for secure connections. You can enforce this by enabling the “Secure transfer required” setting on your storage account.
- Example: A developer connects to Blob Storage from an application. If they try to use http://..., the request will be blocked once secure transfer is required, ensuring only https://... connections are allowed.
- [Double encryption](https://docs.azure.cn/en-us/security/fundamentals/double-encryption#:~:text=Transit%20encryption%20using%20Transport%20Layer,no%20measurable%20link%20latency%20increase.)

##### 🔐 Encryption at Use
- Protects data while it is actively being processed in memory. Unlike encryption at rest or in transit, this is not enabled by default for storage accounts. It requires Azure Confidential Computing features such as Confidential VMs or Always Encrypted with secure enclaves in Azure SQL Database.
- Encryption in use is achieved through Azure Confidential Computing, which leverages hardware-based Trusted Execution Environments (TEEs).
- Example: A financial application runs on an Azure Confidential VM. While sensitive transaction data is processed in memory, it remains encrypted and protected from unauthorized access—even from the cloud provider or system administrators.
- [What is confidential computing?](https://learn.microsoft.com/en-us/azure/confidential-computing/overview)

### Storage Security Framework
##### Least Privilege Access
- **Least Privilege Access**: Grant only the minimum permissions required.
- **Defense in Depth**: Combine SAS, firewalls, identity-based access, and private endpoints.
- **Encryption Everywhere**: Ensure encryption at rest (default), enforce encryption in transit, and use confidential computing for encryption in use.
- **Monitoring & Compliance**: Enable Defender for Storage, logging, and regular audits to detect threats and meet regulatory standards.

