# Security Fundamentals: Core Foundations - Identity & Access Control

## Getting started
For setup instructions, please follow the steps provided in Azure.

### Identity & Access Control
Azure Identity and Access Management (IAM) is the framework Microsoft provides to control who can access Azure resources, how they authenticate, and what they are allowed to do once inside. It is delivered primarily through Microsoft Entra ID.

##### 🔐 Multi-Factor Authentication (MFA)
- Requires all users to register for MFA
- [Configure Microsoft Entra multifactor authentication settings](https://docs.azure.cn/en-us/entra/identity/authentication/howto-mfa-mfasettings)
##### ⛔️ Role-Based Access Control (RBAC)
- Applies at multiple scopes: Management Group, Subscription, Resource Group, and individual resources.
- Enforces least privilege by assigning only necessary permissions (e.g., Virtual Machine Contributor).
- [Grant a user access to Azure resources using the Azure portal](https://learn.microsoft.com/en-us/azure/role-based-access-control/quickstart-assign-role-user-portal)
##### ‌‌‌‌🦱 Service Principals
- Best for external or non‑Azure apps.
- [Register a Microsoft Entra app and create a service principal](https://learn.microsoft.com/en-us/entra/identity-platform/howto-create-service-principal-portal)
##### 🦱 Managed Identity
- Best for Azure-native services.
- Credentials are automatically managed by Azure.
- [Use Azure portal to grant a managed identity access to a resource](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/grant-managed-identity-resource-access-azure-portal)
##### 👨‍👨‍👦‍👦 Microsoft Entra ID Groups
- Enforce group membership practices through central management (e.g., dividing departments to allocate resources effectively).
- [Manage Microsoft Entra groups and group membership](https://docs.azure.cn/en-us/entra/fundamentals/how-to-manage-groups)
##### 💵 Privileged Identity Management (PIM) *(Premium license required)*
- Provides just-in-time elevation for high-privilege roles, meaning users only get admin-level access when they need it, and only for the time required.
- Enforces on-time permission by requiring approval workflows or activation before elevated access is granted.
- Helps reduce standing privileges and includes auditing/alerts to track privileged role activations.
- [Start using Privileged Identity Management](https://docs.azure.cn/en-us/entra/id-governance/privileged-identity-management/pim-getting-started)
##### 💵 Just-in-time (JIT) Access *(Premium license required)*
- Grants temporary, controlled access to Azure resources — not only virtual machines, but also other sensitive workloads and administrative functions.
- Enforces the principle of least privilege by ensuring users only have access for the exact time they need it, reducing standing permissions.
- Can be combined with Privileged Identity Management (PIM) to require approval workflows before granting elevated access.
- [Enable just-in-time access](https://learn.microsoft.com/en-us/azure/defender-for-cloud/enable-just-in-time-access)
### Microsoft Entra Recommendations for Azure Identity Security
##### 🛂 Microsoft Entra Identity Protection *(Premium license required)*
- With Identity Protection, your organization can continuously monitor for vulnerabilities and high‑risk identity activities. Using advanced machine learning, it detects abnormal sign‑ins and flags suspicious user behaviors to safeguard identities.
- [Plan an ID Protection deployment](https://learn.microsoft.com/en-us/entra/id-protection/how-to-deploy-identity-protection)
##### 🔐 Microsoft Entra Privileged Identity Management (PIM) (Premium license required)
- Provides just‑in‑time (JIT) access to Azure AD and Azure resource roles.
- Enforces approval workflows, MFA, and time‑bound access for privileged roles.
- Reduces the risk of standing administrative privileges.
- [Start using Privileged Identity Management](https://docs.azure.cn/en-us/entra/id-governance/privileged-identity-management/pim-getting-started)
##### 🔐 Azure Privileged Access Management (PAM) *(Premium license required)*
- Focuses on controlling and monitoring privileged accounts during sensitive operations.
- Enforces just‑enough‑access (JEA) and approval workflows for elevated tasks.
- Complements PIM by adding an extra layer of control for privileged sessions.
- [Learn about privileged access management](https://learn.microsoft.com/en-us/purview/privileged-access-management)
##### 🔐 Azure Identity and Access Management (IAM)
- The broader umbrella covering:
  - Authentication (sign‑in, MFA, passwordless)
  - Authorization (RBAC, conditional access)
  - Identity governance (lifecycle management, access reviews)
- Ensures the right users have the right access under the right conditions.
- [Grant a user access to Azure resources using the Azure portal](https://learn.microsoft.com/en-us/azure/role-based-access-control/quickstart-assign-role-user-portal)
##### 🔎 Access Reviews *(Premium license required)*
- With Access Reviews in Microsoft Entra ID, organizations can maintain secure and compliant identity governance. Scheduled reviews ensure that only authorized users continue to have access to groups, applications, and roles.
- [Create an access review of groups and applications in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/id-governance/create-access-review)

### Zero Trust IAM Framework
##### 🛡️ Zero Trust Principles for Azure IAM
###### 🔎 Verify Explicitly
- Concept: Never trust, always verify. Authentication and authorization must use all available signals (identity, device health, location, risk, workload).
  - Your Controls:
    - 🔐 Multi-Factor Authentication (MFA)
    - 🦱 Service Principals
    - 🦱 Managed Identities
    - 🛂 Microsoft Entra Identity Protection
    - 🎯 Conditional Access (via Entra)
###### ⛔ Least Privilege Access
- Concept: Limit access to only what is necessary, and only for the time required.
  - Your Controls:
    - ⛔ Role-Based Access Control (RBAC)
    - 👨‍👨‍👦‍👦 Microsoft Entra ID Groups
    - 💵 Privileged Identity Management (PIM)
    - 🔎 Access Reviews
###### 🛡️ Assume Breach
- Concept: Design IAM policies to minimize impact if credentials or accounts are compromised.
  - Your Controls:
    - 💵 Just-in-Time (JIT) VM Access.
    - 📜 Audit Logs & Monitoring (Sentinel, Defender for Cloud)
    - 📊 Identity Secure Score
### Refer to the following links to learn about the various services and technologies mentioned in this article.
- [Zero Trust security in Azure](https://learn.microsoft.com/en-us/azure/security/fundamentals/zero-trust)
- <img width="709" height="378" alt="image" src="https://github.com/user-attachments/assets/c361f72d-6155-45a4-885d-27d1b011f3fd" />
- [Overview – Apply Zero Trust principles to Azure services](https://learn.microsoft.com/en-us/security/zero-trust/apply-zero-trust-azure-services-overview)
