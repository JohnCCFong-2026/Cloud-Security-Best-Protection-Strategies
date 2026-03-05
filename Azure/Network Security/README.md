# Security Fundamentals: Core Foundations - Network Security

## Getting started
For setup instructions, please follow the steps provided in Azure.

### Network Security
Azure provides a layered approach to securing cloud networks. The goal is to protect resources (VMs, databases, apps) from unauthorized access and malicious traffic while allowing legitimate communication.  
This includes tools such as **Network Security Groups (NSGs)**, **Azure Firewall**, **DDoS Protection**, and **Application Security Groups (ASGs)**, all working together to enforce security at different levels.

##### Network Security Group (NSG)
- A Network Security Group (NSG) is a specific security feature in Microsoft Azure that acts like a virtual firewall for controlling inbound and outbound traffic to Azure resources.
- NSGs can be applied to **subnets** (affecting all resources inside) or **network interfaces (NICs)** (affecting individual VMs/resources).
- They contain rules that allow or deny traffic based on source/destination IP, port, and protocol.
- NSGs include **default rules** such as allowing traffic within a virtual network and denying inbound internet traffic unless explicitly permitted.
- [Create, change, or delete a network security group](https://learn.microsoft.com/en-us/azure/virtual-network/manage-network-security-group?tabs=network-security-group-portal)

##### Application Security Group (ASG)
- An Application Security Group (ASG) in Microsoft Azure is a feature that simplifies network security management by grouping virtual machines (VMs) or resources based on their application or workload.
- ASGs allow you to reference groups directly in **Network Security Group (NSG)** rules, eliminating the need to manage individual IP addresses.
- They provide **logical grouping** of resources (e.g., "WebServers", "DatabaseServers") and enable **dynamic membership**, so VMs can be added or removed without modifying NSG rules.
- ASGs make NSG rule management more scalable and easier to maintain in large environments.
- Example: You can create a rule that allows traffic from ASG **WebServers** to ASG **DatabaseServers** on port 1433 (SQL), instead of specifying IP addresses.
- [Application security groups](https://docs.azure.cn/en-us/virtual-network/application-security-groups)
