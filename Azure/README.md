# Security Fundamentals: Core Foundations

## Getting started
For setup instructions, please follow the steps provided in Azure.

### Identity & Access Control
##### 🔐 Multi-Factor Authentication (MFA) for user sign in
- Requires all users to register for MFA
- [Configure Microsoft Entra multifactor authentication settings](https://docs.azure.cn/en-us/entra/identity/authentication/howto-mfa-mfasettings)
##### ⛔️ Role-Based Access Control (RBAC) for Management Group / Subscription / Resource Group / Resource Level:
- Enforces the principle of least privilege by assigning users only the permissions necessary for their roles. For example, virtual machine contributor etc.
- [Grant a user access to Azure resources using the Azure portal](https://learn.microsoft.com/en-us/azure/role-based-access-control/quickstart-assign-role-user-portal)
##### ‌‌‌‌🦱 Service Principal
- Use Service Principals when external apps or automation need Azure access.
- [Register a Microsoft Entra app and create a service principal](https://learn.microsoft.com/en-us/entra/identity-platform/howto-create-service-principal-portal)
##### 🦱 Managed Identity
- Use Managed Identities when Azure services need to talk to each other.
- [Use Azure portal to grant a managed identity access to a resource](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/grant-managed-identity-resource-access-azure-portal)
##### 👨‍👨‍👦‍👦 Microsoft Entra ID
- Enforce group member practices through central management, for example by dividing departments to allocate resources effectively.
- [Manage Microsoft Entra groups and group membership](https://docs.azure.cn/en-us/entra/fundamentals/how-to-manage-groups)
##### 💵 Option: Microsoft Entra Privileged Identity Management (PIM) (License required)
- Requires users to obtain one-time permission for high-privilege requests, applicable to both internal and external users.
- [Start using Privileged Identity Management](https://docs.azure.cn/en-us/entra/id-governance/privileged-identity-management/pim-getting-started)
##### 💵 Option: Just-in-time (JIT) (License required)
- Requires users to obtain one-time access to resources, such as virtual machines.
- [Enable just-in-time access](https://learn.microsoft.com/en-us/azure/defender-for-cloud/enable-just-in-time-access)
##### (Protection) Perform an assessment of identity management security
##### 🛂 Microsoft Entra Identity Protection (License required)
- With Identity Protection, your organization can continuously monitor for vulnerabilities and high‑risk identity activities. Using advanced machine learning, it detects abnormal sign‑ins and flags suspicious user behaviors to safeguard identities.
- [Plan an ID Protection deployment](https://learn.microsoft.com/en-us/entra/id-protection/how-to-deploy-identity-protection)
##### 🔎 Access Reviews (License required)


#### Network security group
 
