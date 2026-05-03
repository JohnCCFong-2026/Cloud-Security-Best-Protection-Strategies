# Security Fundamentals: Core Foundations - Host Security

## Getting started
For setup instructions, please follow the steps provided in AWS.

### Host Security
AWS host security focuses on safeguarding the compute environment, including EC2 instances and workloads, through layered protections. Core measures include instance hardening, patch management, identity and access controls, encryption, monitoring, and intrusion detection.

##### 🛡️ Amazon EBS Encryption (Nitro System)
- Provides seamless, hardware-accelerated encryption for data at rest and in transit between the host and storage.
- Example: On Nitro-based instances, encryption is handled by dedicated hardware, ensuring there is zero impact on the CPU performance of your application while keeping your disks secure.

##### 🧠 AWS Nitro Enclaves
- Creates isolated compute environments to protect and process highly sensitive "data in use" (data in memory).
- Example: A healthcare app processes sensitive patient data inside a Nitro Enclave. This environment has no persistent storage or interactive access, ensuring even a "root" administrator cannot see the data being processed.

##### 🔒 Amazon EC2 Security Groups & Network ACLs
- Control inbound and outbound traffic to your instances, acting as virtual firewalls.
- A company restricts SSH access to EC2 instances by allowing only connections from its corporate IP range.

##### 🔧 AWS Systems Manager Patch Manager
- Automates patching for operating systems and applications on EC2 instances.
- Example: An e-commerce platform schedules automatic patching of Linux servers every Sunday night to reduce downtime.

##### 👤 AWS Identity and Access Management (IAM)
- Fine-grained access control for AWS resources, including EC2 instances.
- Example: Developers are given IAM roles that allow them to start/stop EC2 instances but not modify security groups.

### Recommendations for AWS Host Security
##### 🛡️ OS‑Level Hardening
- Securing the operating system inside the EC2 instance.
- Actions:
  - Disable unused services and ports
  - Enforce SSH key‑based authentication
  - Apply CIS benchmark configurations (Linux/Windows)
  - Configure host‑based firewalls (iptables, Windows Firewall)
- Example: A company applies CIS Linux benchmarks, disables legacy protocols like Telnet, and enforces SSH key authentication.

##### 🛡️ Cloud‑Level Hardening
- Securing the instance using AWS‑native controls and services.
- Actions:
  - 🔒 Amazon EC2 Security Groups & Network ACLs → firewall‑like traffic control
  - 👤 AWS Identity and Access Management (IAM) → least‑privilege access policies
  - 🕵️ Amazon GuardDuty → intrusion detection and anomaly detection
  - 🛡️ AWS Security Hub → compliance checks against CIS, PCI DSS, etc.
-Example: A company restricts SSH access to EC2 instances using Security Groups, assigns IAM roles to limit developer permissions, and enables GuardDuty to detect suspicious activity.

### Host Security Framework (3 Pillars)
- 🔒 Protection
  - Safeguarding EC2 instances and their data against malware, unauthorized access, and breaches.
  - Includes:
    - 🛡️ Amazon EBS Encryption (Nitro System) – seamless hardware‑accelerated encryption for data at rest and in transit.
    - 🧠 AWS Nitro Enclaves – isolated compute environments for sensitive “data in use.”
    - 🔒 Amazon EC2 Security Groups & Network ACLs – firewall‑like controls for inbound/outbound traffic.
    - 👤 AWS Identity and Access Management (IAM) – least‑privilege access controls.
  - Example: We enabled EBS encryption on all EC2 volumes, deployed Nitro Enclaves for sensitive healthcare workloads, and restricted SSH access using Security Groups to allow only corporate IP ranges.
- 🔄 Maintenance
  - nsuring operating systems remain secure and compliant by keeping them up to date.
  - Includes:
    - 🔧 AWS Systems Manager Patch Manager – automated patching across Windows and Linux EC2 instances.
    - 📊 Amazon CloudWatch & AWS CloudTrail – monitoring and logging for visibility and compliance.
  - Example: We configured Patch Manager to apply monthly security updates to all EC2 instances, while CloudWatch alarms and CloudTrail logs provide real‑time monitoring and audit trails.
- 🛠️ Hardening
  - Strengthening the operating system and instance configuration to reduce attack surfaces.
  - Includes:
    - 🛡️ EC2 OS Hardening (CIS Benchmarks) – disable unused services, enforce SSH key authentication, apply secure baselines.
    - 🕵️ Amazon GuardDuty – intrusion detection and threat monitoring.
    - 🛡️ AWS Security Hub – continuous compliance checks against CIS, PCI DSS, and other standards.
  - Example: We hardened our Linux EC2 instances by applying CIS benchmark configurations, enforced SSH key‑based authentication, and enabled GuardDuty with Security Hub to continuously monitor compliance and detect suspicious activity.
