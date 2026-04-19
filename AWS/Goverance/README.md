# Security Fundamentals: Core Foundations - Governance

## Getting started
For setup instructions, please follow the steps provided in Azure.

### Governance
AWS Governance refers to the set of policies, processes, and tools that organizations use to manage, secure, and control their resources in Amazon Web Services. It ensures that cloud usage aligns with business requirements, regulatory standards, and security best practices.

##### 🏢 AWS Organizations
- Centralized multi‑account governance.
- Manage policies, billing, and compliance across accounts.
- Example: Apply Service Control Policies (SCPs) to block risky services in production.

##### 🔒 Compliance & Security Monitoring
- Tools: AWS Config, Security Hub, CloudTrail.
- Ensures resources meet standards and regulations.
- Example: Config checks if all S3 buckets are encrypted, alerts on non‑compliance.

##### 💰 Cost Management
- Tools: AWS Budgets, Cost Explorer, Trusted Advisor.
- Track and optimize spending.
- Example: Budget alert when EC2 costs exceed $10,000/month.

##### 🏷️ Resource Management & Tagging
- Standardized tagging for ownership, environment, and compliance.
- Example: EC2 instance tagged with “Owner: Team A” and “Environment: Production”.

##### ⚙️ Automation & Policy Enforcement
- Tools: AWS Control Tower, CloudFormation, Service Catalog.
- Automates account setup and enforces guardrails.
- Example: Control Tower ensures new accounts comply with organizational policies
