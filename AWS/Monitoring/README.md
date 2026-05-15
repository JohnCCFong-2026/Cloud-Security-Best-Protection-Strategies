# Security Fundamentals: Core Foundations - Monitoring

## Getting started
For setup instructions, please follow the steps provided in AWS.

### Monitoring
AWS monitoring ensures visibility, performance tracking, and security oversight across your cloud environment. Core foundations include real-time metrics, centralized logging, automated alarms, and activity auditing. Together, these capabilities help detect anomalies, maintain compliance, and optimize workloads.

##### 🔒 AWS GuardDuty
- Continuous threat detection service that monitors logs, VPC flow, DNS, and CloudTrail events.
- Example: GuardDuty detects anomalous API calls suggesting credential compromise, triggering an automated incident response workflow.
- [Security in Amazon GuardDuty](https://docs.aws.amazon.com/guardduty/latest/ug/security.html)

##### 📜 AWS CloudTrail
- Records all API calls for auditing and forensic analysis.
- Example: A bank investigates unauthorized access attempts by reviewing CloudTrail logs to trace the source of suspicious activity.
- [Security in AWS CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/WhatIsCloudTrail-Security.html)

##### 🛡️ AWS Security Hub CSPM
- Centralizes security findings from multiple AWS services (Inspector, GuardDuty, Macie).
- Example: A retail company uses Security Hub dashboards to prioritize remediation of critical vulnerabilities across workloads.
- [Security in AWS Security Hub CSPM](https://docs.aws.amazon.com/securityhub/latest/userguide/security.html)

##### 📡 Amazon CloudWatch
- Real-time monitoring and alerting.
- Example: Triggers alarms when unusual traffic patterns occur.
- [Security in Amazon CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/security.html)

##### 🔍 AWS Detective
- Investigates and visualizes security findings.
- Capabilities: Helps analyze relationships between resources and events.
- Example: Tracing the root cause of suspicious API activity across multiple accounts.
- [Security in Amazon Detective](https://docs.aws.amazon.com/detective/latest/userguide/security.html)

##### 💡 AWS Trusted Advisor
- Provides best-practice recommendations for cost, performance, security, and fault tolerance.
- Identifies underutilized resources, insecure configurations, and optimization opportunities.
- Example: Suggesting resizing EC2 instances to reduce costs.
- [Viewing AWS Security Hub CSPM controls in AWS Trusted Advisor](https://docs.aws.amazon.com/awssupport/latest/user/security-hub-controls-with-trusted-advisor.html)

##### 💰 AWS Cost Explorer
- Monitors and analyzes cloud spending.
- Provides cost reports, forecasts, and optimization insights.
- Example: Identifying rising costs due to unused EBS volumes and recommending cleanup.
- [Security in AWS Cost Management](https://docs.aws.amazon.com/cost-management/latest/userguide/security.html)

##### 🏥 AWS Personal Health Dashboard
- Provides alerts and remediation guidance when AWS services experience issues.
- Personalized view of AWS service health affecting your resources.
- Example: Notifying admins when an outage impacts RDS in a specific region.
- [Viewing your account events in the AWS Health Dashboard](https://docs.aws.amazon.com/health/latest/ug/aws-health-account-views.html)

### Recommendations for AWS Monitoring

### Monitoring Framework
