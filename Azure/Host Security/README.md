# Security Fundamentals: Core Foundations - Host Security

## Getting started
For setup instructions, please follow the steps provided in Azure.

### Host Security
Azure host security focuses on protecting the virtual machines (VMs), operating systems, and compute resources that run workloads in the cloud. The goal is to ensure that the underlying hosts are hardened against threats, monitored for suspicious activity, and compliant with security standards.

##### 🛡️ VM Endpoint Protection 
- Azure integrates with Microsoft Defender for Endpoint to provide antimalware and endpoint detection capabilities. This helps protect VMs against viruses, ransomware, and suspicious activity. Administrators can enable endpoint protection directly from the Azure portal or through Azure Security Center, ensuring that every VM has real-time monitoring and threat response.
- Example: In Azure, we enabled Microsoft Defender for Endpoint on all virtual machines to provide real-time antimalware protection and detect suspicious activity across our workloads.

##### 🔄 Update Management Solution
-  Using Azure Automation Update Management, you can schedule and deploy operating system patches across Windows and Linux VMs. This ensures hosts remain secure against known vulnerabilities. The solution provides compliance reporting, centralized control, and the ability to automate patch cycles without disrupting workloads.
-  Example: Our team uses Azure Automation Update Management to schedule monthly patch deployments, ensuring that both Windows and Linux VMs remain compliant and protected against known vulnerabilities.

##### Azure Disk Encryption (ADE)  
- ADE uses BitLocker (Windows) and DM-Crypt (Linux) to encrypt VM disks at rest. This protects sensitive data stored on OS and data disks from unauthorized access. Encryption keys are managed securely in Azure Key Vault, giving organizations full control over key rotation and access policies.
- Example: We applied Azure Disk Encryption to our VM disks, with keys stored in Azure Key Vault, so that sensitive data at rest is fully secured using BitLocker for Windows and DM-Crypt for Linux.

##### 💾 Encrypt at Host
- Encrypt at Host is a security feature in Azure that ensures all data is encrypted at the compute layer before it leaves the VM host and travels to Azure Storage. Unlike Azure Disk Encryption (ADE), which encrypts disks inside the VM using BitLocker or DM-Crypt, Encrypt at Host works transparently at the infrastructure level.
- Example: In Azure, we enabled Encrypt at Host for our virtual machines so that all data is automatically encrypted at the compute layer before leaving the host, providing strong protection without requiring disk-level encryption management.


