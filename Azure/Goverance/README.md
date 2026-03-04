# Security Fundamentals: Core Foundations - Governance

## Getting started
For setup instructions, please follow the steps provided in Azure.

### Governance
Azure Governance refers to the set of policies, processes, and tools that organizations use to manage, secure, and control their resources in Microsoft Azure. It ensures that cloud usage aligns with business requirements, regulatory standards, and security best practices.

#####  🔧 Azure Polices
- Enforce compliance by ensuring that resources meet both conditional and mandatory standards, keeping them aligned with your organization’s corporate requirements.
- [Create a policy assignment to identify non-compliant resources using Azure portal](https://learn.microsoft.com/en-us/azure/governance/policy/assign-policy-portal)
#####  🔒 Security Polices
- Enforce compliance with global standards and regulatory frameworks, including NIST, HIPAA, and other industry benchmarks, ensuring that cloud resources remain secure and aligned with organizational requirements.
- [Azure Policy built-ins](https://learn.microsoft.com/en-us/azure/governance/policy/samples/?context=%2Fazure%2Fgovernance%2Fpolicy%2Fcontext%2Fpolicy-context)
##### 💵 Cost Management
- Monitor and track costs within Azure. For example, if daily costs increase unexpectedly beyond normal usage patterns, it may indicate a potential attack.
- [Start using Cost Analysis](https://learn.microsoft.com/en-us/azure/cost-management-billing/costs/quick-acm-cost-analysis)
##### ☁️ Defender for Cloud (Basic is free and Premium license required)
- Continuously assesses resources to improve security posture with secure score and recommendations.
- Provides threat protection for workloads (VMs, databases, containers, storage).
- Supports regulatory compliance and extends protection to multicloud/hybrid environments.
- [Connect your Azure subscriptions](https://learn.microsoft.com/en-us/azure/defender-for-cloud/connect-azure-subscription)
### Goverance Framework
##### 🧩 Cloud Adoption Framework (CAF) for Azure
- Provides best practices, guidance, and tools to help organizations plan, implement, and manage their cloud adoption journey effectively.
- Focuses on the cloud adoption journey (strategy, plan, ready, adopt, govern, manage). Governance is one of its pillars, ensuring compliance, security, and cost control across domains.
- [What is the Microsoft Cloud Adoption Framework?](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/overview#cloud-adoption-framework-scenarios)
##### 🧩 Well-Architected Framework (WAF) for Azure
- Focuses on workload design and architecture. It provides best practices across five pillars:
- Cost Optimization
- Operational Excellence
- Performance Efficiency
- Reliability
- Security
- [Microsoft Azure Well-Architected Framework pillars](https://learn.microsoft.com/en-us/azure/well-architected/pillars)
