# Security Fundamentals: Core Foundations - Host Security

## Getting started
For setup instructions, please follow the steps provided in Azure.

### Host Security
Azure host security focuses on protecting the virtual machines (VMs), operating systems, and compute resources that run workloads in the cloud. The goal is to ensure that the underlying hosts are hardened against threats, monitored for suspicious activity, and compliant with security standards.

##### 🛡️ VM Endpoint Protection
- Azure integrates with Microsoft Defender for Endpoint to provide antimalware and endpoint detection capabilities. This helps protect VMs against viruses, ransomware, and suspicious activity. Administrators can enable endpoint protection directly from the Azure portal or through Azure Security Center, ensuring that every VM has real-time monitoring and threat response.
- Example: In Azure, we enabled Microsoft Defender for Endpoint on all virtual machines to provide real-time antimalware protection and detect suspicious activity across our workloads.
- [Sign up for Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/defender-vulnerability-management/get-defender-vulnerability-management)

##### 🔄 Update Management Solution
-  Using Azure Automation Update Management, you can schedule and deploy operating system patches across Windows and Linux VMs. This ensures hosts remain secure against known vulnerabilities. The solution provides compliance reporting, centralized control, and the ability to automate patch cycles without disrupting workloads.
-  Example: Our team uses Azure Automation Update Management to schedule monthly patch deployments, ensuring that both Windows and Linux VMs remain compliant and protected against known vulnerabilities.
- [How Update Manager works](https://learn.microsoft.com/en-us/azure/update-manager/workflow-update-manager?tabs=azure-vms%2Cupdate-win)

##### 💾 Azure Disk Encryption (ADE)
- ADE uses BitLocker (Windows) and DM-Crypt (Linux) to encrypt VM disks at rest. This protects sensitive data stored on OS and data disks from unauthorized access. Encryption keys are managed securely in Azure Key Vault, giving organizations full control over key rotation and access policies.
- Example: We applied Azure Disk Encryption to our VM disks, with keys stored in Azure Key Vault, so that sensitive data at rest is fully secured using BitLocker for Windows and DM-Crypt for Linux.
- [Azure Disk Encryption scenarios on Windows VMs](https://learn.microsoft.com/en-us/azure/virtual-machines/windows/disk-encryption-windows)

##### 🖥 Encrypt at Host
- Encrypt at Host is a security feature in Azure that ensures all data is encrypted at the compute layer before it leaves the VM host and travels to Azure Storage. Unlike Azure Disk Encryption (ADE), which encrypts disks inside the VM using BitLocker or DM-Crypt, Encrypt at Host works transparently at the infrastructure level.
- Example: In Azure, we enabled Encrypt at Host for our virtual machines so that all data is automatically encrypted at the compute layer before leaving the host, providing strong protection without requiring disk-level encryption management.
- [Use the Azure portal to enable end-to-end encryption using encryption at host](https://learn.microsoft.com/en-us/azure/virtual-machines/disks-enable-host-based-encryption-portal?tabs=azure-powershell)

### Recommendations for Azure Host Security
##### 🛡️ Hardening (Windows/Linux OS) in Operating System (OS)
- System hardening in Azure involves securing the operating system inside the VM itself. For both Windows and Linux, this means applying recommended security baselines, disabling unnecessary services, closing unused ports, enforcing strong authentication, and configuring host-based firewalls. Azure provides guidance and built-in baselines through Microsoft Defender for Cloud to help ensure VMs are aligned with best practices.
- Example: We hardened our Windows and Linux VMs by applying Azure Security Baselines, disabling legacy protocols, and configuring host-based firewalls to block unused ports, thereby reducing vulnerabilities inside the system itself.
- [Windows and Linux Server Hardening: Comprehensive Checklist](https://www.liquidweb.com/blog/server-hardening-checklist/) by Marho Atumu

##### 🛡️ Hardening (Windows/Linux OS) in Azure Cloud
- Azure offers official security baselines for virtual machines, tailored to both Windows and Linux environments. These baselines provide prescriptive guidance on secure configurations, covering areas such as identity management, network security, logging, and monitoring. By following these baselines, organizations can ensure their VMs meet Azure’s recommended security standards.
- Example: We aligned our Linux VMs with the Azure Security Baseline for Virtual Machines, implementing recommended identity controls, enabling auditing, and applying secure configuration settings to strengthen our cloud-hosted workloads.
- [Azure security baseline for Virtual Machines - Linux Virtual Machines](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/virtual-machines-linux-virtual-machines-security-baseline)

### Host Security Framework (3 Pillars)
- 🔒 Protection
  - This pillar focuses on safeguarding virtual machines (VMs) and their data against malware, unauthorized access, and breaches. It includes endpoint protection tools, encryption at the disk level (Azure Disk Encryption), and encryption at the host level to ensure data remains secure both at rest and in use.
  - Example: We deployed Microsoft Defender for Endpoint on our VMs to detect and block malware, enabled Azure Disk Encryption (ADE) to protect sensitive data at rest, and activated Encrypt at Host to ensure all VM data is encrypted during processing.

- 🔄 Maintenance
  - Maintenance ensures that operating systems remain secure and compliant by keeping them up to date. Azure Update Management helps automate patching across Windows and Linux VMs, reducing vulnerabilities and maintaining a strong security posture.
  - Example: We configured Azure Update Management to automatically apply monthly security patches to all Windows and Linux VMs, ensuring that known vulnerabilities are addressed promptly and compliance requirements are met.

- 🛠️ Hardening
  - Hardening strengthens the internal operating system by reducing its attack surface. This involves applying Windows/Linux security baselines, disabling unnecessary services, closing unused ports, enforcing strong authentication, and configuring host-based firewalls. Azure provides official security baselines and recommendations through Microsoft Defender for Cloud.
  - Example: We hardened our Linux VMs by applying Azure’s security baseline, disabling legacy protocols like Telnet, enforcing SSH key-based authentication, and configuring host-based firewalls to block unused ports, thereby reducing potential entry points for attackers.
