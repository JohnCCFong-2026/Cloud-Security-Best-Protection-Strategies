# Security Fundamentals: Core Foundations

## Getting started
For setup instructions, please follow the steps provided in Azure.

### Identity & Access Control
##### 🔐 Multi-Factor Authentication (MFA) for user sign in
- Requires all users to register for MFA
- [Configure Microsoft Entra multifactor authentication settings](https://docs.azure.cn/en-us/entra/identity/authentication/howto-mfa-mfasettings)
##### ⛔️ Role-Based Access Control (RBAC) applies at multiple scopes: Management Group, Subscription, Resource Group, and individual resources
- Enforces the principle of least privilege by assigning users only the permissions necessary for their roles. For example, virtual machine contributor etc.
- [Grant a user access to Azure resources using the Azure portal](https://learn.microsoft.com/en-us/azure/role-based-access-control/quickstart-assign-role-user-portal)
##### ‌‌‌‌🦱 Service Principals
- Service Principals are best for external or non‑Azure apps.
- [Register a Microsoft Entra app and create a service principal](https://learn.microsoft.com/en-us/entra/identity-platform/howto-create-service-principal-portal)
##### 🦱 Managed Identity
- Managed Identities are best for Azure-native services.
- [Use Azure portal to grant a managed identity access to a resource](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/grant-managed-identity-resource-access-azure-portal)
##### 👨‍👨‍👦‍👦 Microsoft Entra ID
- Enforce group member practices through central management, for example by dividing departments to allocate resources effectively.
- [Manage Microsoft Entra groups and group membership](https://docs.azure.cn/en-us/entra/fundamentals/how-to-manage-groups)
##### 💵 Microsoft Entra Privileged Identity Management (PIM) (Premium license required)
- Requires users to obtain one-time permission for high-privilege requests, applicable to both internal and external users.
- [Start using Privileged Identity Management](https://docs.azure.cn/en-us/entra/id-governance/privileged-identity-management/pim-getting-started)
##### 💵 Just-in-time (JIT) (Premium license required)
- Requires users to obtain one-time access to resources, such as virtual machines.
- [Enable just-in-time access](https://learn.microsoft.com/en-us/azure/defender-for-cloud/enable-just-in-time-access)
### Review Microsoft Entra recommendations (such as Identity Secure Score) to assess and improve your identity management security posture.
##### 🛂 Microsoft Entra Identity Protection (Premium license required)
- With Identity Protection, your organization can continuously monitor for vulnerabilities and high‑risk identity activities. Using advanced machine learning, it detects abnormal sign‑ins and flags suspicious user behaviors to safeguard identities.
- [Plan an ID Protection deployment](https://learn.microsoft.com/en-us/entra/id-protection/how-to-deploy-identity-protection)
##### 🔎 Access Reviews (Premium license required)
- With Access Reviews in Microsoft Entra ID, organizations can maintain secure and compliant identity governance. Scheduled reviews ensure that only authorized users continue to have access to groups, applications, and roles.
- [Create an access review of groups and applications in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/id-governance/create-access-review)
### Zero Trust IAM Framework
##### 🛡️ Zero Trust Principles for Azure IAM
###### 🔎 Verify Explicitly
- Concept: Never trust, always verify. Authentication and authorization must use all available signals (identity, device health, location, risk, workload).
###### Your Controls
- 🔐 Multi-Factor Authentication (MFA)
- 🦱 Service Principals
- 🦱 Managed Identities
- 🛂 Microsoft Entra Identity Protection
- 🎯 Conditional Access (via Entra)
###### ⛔ Least Privilege Access
- Concept: Limit access to only what is necessary, and only for the time required.
###### Your Controls
- ⛔ Role-Based Access Control (RBAC)
- 👨‍👨‍👦‍👦 Microsoft Entra ID Groups
- 💵 Privileged Identity Management (PIM)
- 🔎 Access Reviews
###### 🛡️ Assume Breach
- Concept: Design IAM policies to minimize impact if credentials or accounts are compromised.
###### Your Controls
- 💵 Just-in-Time (JIT) VM Access.
- 📜 Audit Logs & Monitoring (Sentinel, Defender for Cloud)
- 📊 Identity Secure Score
