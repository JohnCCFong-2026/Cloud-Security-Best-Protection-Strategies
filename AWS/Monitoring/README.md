# Security Fundamentals: Core Foundations - Monitoring

## Getting started
For setup instructions, please follow the steps provided in AWS.

### Monitoring
AWS monitoring ensures visibility, performance tracking, and security oversight across your cloud environment. Core foundations include real-time metrics, centralized logging, automated alarms, and activity auditing. Together, these capabilities help detect anomalies, maintain compliance, and optimize workloads.

##### 🔒 AWS GuardDuty
- Continuous threat detection service that monitors logs, VPC flow, DNS, and CloudTrail events.
- Example: GuardDuty detects anomalous API calls suggesting credential compromise, triggering an automated incident response workflow.

##### 📜 AWS CloudTrail
- Records all API calls for auditing and forensic analysis.
- Example: A bank investigates unauthorized access attempts by reviewing CloudTrail logs to trace the source of suspicious activity.

##### 🛡️ AWS Security Hub
- Centralizes security findings from multiple AWS services (Inspector, GuardDuty, Macie).
- Example: A retail company uses Security Hub dashboards to prioritize remediation of critical vulnerabilities across workloads.

##### 📡 CloudWatch
- Real-time monitoring and alerting.
- Example: Triggers alarms when unusual traffic patterns occur.
