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

##### 🛡️ AWS Config
- Tracks resource configurations and evaluates them against compliance rules.
- Example: Flagging an S3 bucket that is publicly accessible and recommending remediation.

##### 🔍 Amazon OpenSearch Service
- Centralized log analytics and search engine for observability.
- Example: Querying failed login attempts across multiple accounts to detect brute-force attacks.
- [Security in Amazon OpenSearch Service](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/security.html)

##### 📥 AWS Distro for OpenTelemetry
- Open-source distribution for collecting telemetry data (metrics, logs, traces) from applications.
- Example: Exporting application traces to X-Ray and metrics to CloudWatch for unified observability.
- [AWS Distro for OpenTelemetry](https://aws-otel.github.io/)

##### 🔎 AWS X-Ray
- Provides distributed tracing to analyze performance bottlenecks in applications.
- Example: Detecting that a web app’s slow response is caused by a specific database query.
- [Security in AWS X-Ray](https://docs.aws.amazon.com/xray/latest/devguide/security.html)

### Recommendations for AWS Monitoring
##### 📈 Amazon Managed Grafana (pricing required)
- Fully managed Grafana dashboards for visualization of metrics and logs.
- Example: Creating a dashboard showing real-time traffic, latency, and error rates for an e-commerce site.

##### 📊 Amazon Managed Service for Prometheus (pricing required)
- Managed Prometheus service for collecting and querying metrics from containerized workloads (EKS, ECS).
- Example: Monitoring Kubernetes pods and triggering alerts when memory usage exceeds thresholds.

### Monitoring Framework (7 Pillars)
##### 📥 Data Collection  
- Gather metrics, logs, and traces from AWS resources and applications.
- Tools: CloudWatch, CloudTrail, VPC Flow Logs.
- Example: Collecting CPU usage metrics from EC2 and transaction traces from a web app.

##### 🗄️ Centralized Storage  
- Store monitoring data in a single place for querying and correlation.
- Tools: CloudWatch Logs, S3, or external SIEM integration.
- Example: Aggregating logs from multiple accounts to detect failed login attempts.

##### 📊 Visualization  
- Turn raw data into dashboards and reports for real-time insights.
- Tools: CloudWatch Dashboards, QuickSight.
- Example: A dashboard showing live traffic, latency, and error rates for an e-commerce site.

##### 🔔 Alerting & Automation  
- Set thresholds and automate responses when issues occur.
- Tools: CloudWatch Alarms, SNS, EventBridge, Lambda.
- Example: Sending an SMS to admins when a critical API fails, and triggering a Lambda function to restart the service.

##### 🛡️ Security Integration  
- Monitor compliance and detect threats.
- Tools: Security Hub, GuardDuty, Inspector, Macie.
- Example: Flagging an S3 bucket exposed to the internet without encryption and recommending remediation.

##### 🕵️ Threat Intelligence & Response  
- Advanced detection, investigation, and automated response to incidents.
- Tools: GuardDuty, Detective, Security Hub + EventBridge automation.
- Example: Detecting suspicious login attempts from multiple countries, correlating them with known attack patterns, and automatically disabling compromised IAM credentials.

##### 💡 Optimization  
- Use recommendations to improve cost, performance, reliability, and security.
- Tools: Trusted Advisor, Cost Explorer.
- Example: Suggesting resizing underutilized EC2 instances to save costs or enabling multi-AZ redundancy for RDS databases.
