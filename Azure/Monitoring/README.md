# Security Fundamentals: Core Foundations - Monitoring

## Getting started
For setup instructions, please follow the steps provided in Azure.

### Monitoring
Azure Monitoring refers to the collection of tools, services, and processes that allow organizations to observe, analyze, and respond to the performance and health of their resources in Microsoft Azure. It ensures that applications, infrastructure, and services are running reliably, securely, and efficiently by providing visibility into metrics, logs, and alerts.

##### 📊 Azure Monitor
- Collects metrics, logs, and traces from Azure resources, applications, and hybrid systems.
- Provides dashboards, alerts, and automated actions.
- Example: Monitoring a VM’s CPU usage and sending an alert if it exceeds 80%.
- [Monitor Azure resources with Azure Monitor](https://learn.microsoft.com/en-us/azure/azure-monitor/platform/monitor-azure-resource)

##### 🛡️ Microsoft Defender for Cloud *(basic tier)*
- Focuses on security monitoring and compliance.
- Detects threats and provides recommendations to strengthen security posture.
- Example: Identifying that a VM is exposed to the internet without firewall rules.
- Monitor Azure resources with Azure Monitor](https://learn.microsoft.com/en-us/azure/azure-monitor/platform/monitor-azure-resource)

##### 📜 Log Analytics
- Centralized workspace for storing and querying logs using Kusto Query Language (KQL).
- Example: Querying failed login attempts across multiple resources.

##### ⚙️ Application Insights
- Specialized monitoring for applications.
- Tracks performance, dependencies, and user behavior.
- Example: Detecting slow response times in a web app and pinpointing the database query causing delays.

##### 🔔 Alerts & Action Groups
- Automated notifications when thresholds or conditions are met.
- Example: Sending an SMS to admins when a critical service goes down.

##### 📊 Workbooks & Dashboards
- Visualize metrics and logs in customizable reports.
- Example: Creating a dashboard showing real-time traffic, latency, and error rates.

##### 💡 Azure Advisor
- Provides personalized recommendations based on monitoring data.
- Helps optimize cost, performance, reliability, and security.
- Example: Suggesting resizing underutilized VMs, enabling geo-redundancy, or applying encryption.

### Recommendations for Azure Monitoring
##### Microsoft Sentinel *(pricing required)*
- A cloud-native SIEM (Security Information and Event Management) and SOAR (Security Orchestration, Automation, and Response) solution.
- Collects and correlates security data across Azure, on-premises, and multi-cloud environments.
- Uses AI and threat intelligence to detect, investigate, and respond to incidents.
- Example: Detecting suspicious login attempts across multiple regions, correlating them with known attack patterns, and automatically disabling compromised accounts.

### Monitoring Framework (7 Pillars)
##### 📥 Data Collection
- Gathering metrics, logs, and traces from Azure resources and applications.
- Tools: Azure Monitor, Application Insights.
- Example: Collecting CPU usage metrics from VMs and transaction traces from a web app.

##### 🗄️ Centralized Storage
- Storing monitoring data in a single place for querying and correlation.
- Tools: Log Analytics Workspace.
- Example: Aggregating logs from multiple VMs to detect failed login attempts across the environment.

##### 📊 Visualization
- Turning raw data into dashboards and reports for real-time insights.
- Tools: Workbooks, Dashboards.
- Example: A dashboard showing live traffic, latency, and error rates for an e-commerce site.

##### 🔔 Alerting & Automation
- Setting thresholds and automating responses when issues occur.
- Tools: Alerts, Action Groups.
- Example: Sending an SMS to admins when a critical API fails, and triggering an automated script to restart the service.

##### 🛡️ Security Integration
- Monitoring compliance and detecting threats.
- Tools: Microsoft Defender for Cloud.
- Example: Flagging a VM exposed to the internet without proper firewall rules and recommending remediation.

##### 🕵️ Threat Intelligence & Response
- Advanced detection, investigation, and automated response to security incidents.
- Tools: Microsoft Sentinel (pricing required).
- Example: Detecting suspicious login attempts from multiple countries, correlating them with known attack patterns, and automatically disabling compromised accounts.

##### 💡 Optimization
- Using recommendations to improve cost, performance, reliability, and security.
- Tools: Azure Advisor.
- Example: Suggesting resizing underutilized VMs to save costs or enabling geo-redundancy for databases.
