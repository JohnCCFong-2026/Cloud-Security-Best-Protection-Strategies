# Security Fundamentals: Core Foundations

## Getting started
For setup instructions, please follow the steps provided in Azure.

### Identity & Access Control
#### 🔐 Multi-Factor Authentication (MFA) for user sign in**
- Requires all users to register for MFA
- [Configure Microsoft Entra multifactor authentication settings](https://docs.azure.cn/en-us/entra/identity/authentication/howto-mfa-mfasettings)
#### ⛔️ Role-Based Access Control (RBAC) for Subscription / Resource Group / Resource Level:**
- Enforces the principle of least privilege by assigning users only the permissions necessary for their roles. For example, virtual machine contributor etc.
- [Grant a user access to Azure resources using the Azure portal](https://learn.microsoft.com/en-us/azure/role-based-access-control/quickstart-assign-role-user-portal)
#### 💵 Option: Microsoft Entra Privileged Identity Management (license required)
- Requires users to obtain one-time permission for high-privilege requests, applicable to both internal and external users.
- [Start using Privileged Identity Management](https://docs.azure.cn/en-us/entra/id-governance/privileged-identity-management/pim-getting-started)


#### Network security group
 
