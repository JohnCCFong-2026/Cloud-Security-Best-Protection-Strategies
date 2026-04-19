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

### Recommendations for AWS Goverance
##### 🧩 AWS Control Tower (Enterprise Setup)
- AWS Control Tower automates the setup of a secure, compliant multi‑account AWS environment (landing zone) using AWS best practices. It orchestrates services like AWS Organizations and IAM Identity Center to manage, govern, and monitor accounts with preconfigured controls (guardrails).
  - Multi‑Account Management — Simplifies creating and managing multiple AWS accounts under a single organization.
  - Preconfigured Guardrails — Enforces security, compliance, and operational policies automatically.
  - Centralized Logging — Implements centralized logging and monitoring across accounts for visibility.
  - Rapid Deployment — Ideal for quickly deploying secure environments at scale.
  - Compliance at Scale — Ensures accounts remain aligned with organizational and regulatory requirements.
- Example: A financial services company uses Control Tower to automatically provision new accounts with encryption enabled, centralized logging configured, and Service Control Policies applied — ensuring compliance without manual setup.

### Goverance Framework
##### 📘 AWS Cloud Adoption Framework (CAF)
- Provides best practices and structured guidance for cloud adoption.
- Six perspectives: Business, People, Governance, Platform, Security, Operations.
- The Governance Perspective ensures compliance, risk management, and accountability.
- Example: A bank uses CAF Governance to define policies for account creation, cost controls, and compliance reporting before migrating workloads.

##### 🏗️ AWS Well‑Architected Framework (WAF)
- Focuses on workload design and architecture best practices.
  - Six pillars:
    - Security
    - Performance Efficiency
    - Cost Optimization
    - Operational Excellence
    - Reliability
    - Sustainability
- Example: A healthcare workload enforces encryption, IAM least privilege, and monitoring under the Security pillar.

##### 🏢 AWS Organizations + SCPs
- Core governance mechanism for multi‑account environments.
- Service Control Policies (SCPs) enforce rules across accounts.
- Example: A retail company restricts production accounts from using unapproved services, ensuring compliance with internal policies.
