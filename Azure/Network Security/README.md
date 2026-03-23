# Security Fundamentals: Core Foundations - Network Security

## Getting started
For setup instructions, please follow the steps provided in Azure.

### Network Security
Azure provides a layered approach to securing cloud networks. The goal is to protect resources (VMs, databases, apps) from unauthorized access and malicious traffic while allowing legitimate communication.  
This includes tools such as **Network Security Groups (NSGs)**, **Azure Firewall**, **DDoS Protection**, and **Application Security Groups (ASGs)**, all working together to enforce security at different levels.

##### 🛂 Network Security Group (NSG)
- A Network Security Group (NSG) is a specific security feature in Microsoft Azure that acts like a virtual firewall for controlling inbound and outbound traffic to Azure resources.
- NSGs can be applied to **subnets** (affecting all resources inside) or **network interfaces (NICs)** (affecting individual VMs/resources).
- They contain rules that allow or deny traffic based on source/destination IP, port, and protocol.
- NSGs are **stateful**: if traffic is allowed in one direction, the return traffic is automatically allowed.
- NSGs include **default rules** such as allowing traffic within a virtual network and denying inbound internet traffic unless explicitly permitted.
- [Create, change, or delete a network security group](https://learn.microsoft.com/en-us/azure/virtual-network/manage-network-security-group?tabs=network-security-group-portal)

##### 🛂 Application Security Group (ASG)
- An Application Security Group (ASG) in Microsoft Azure is a feature that simplifies network security management by grouping virtual machines (VMs) or resources based on their application or workload.
- ASGs allow you to reference groups directly in **Network Security Group (NSG)** rules, eliminating the need to manage individual IP addresses.
- They provide **logical grouping** of resources (e.g., "WebServers", "DatabaseServers") and enable **dynamic membership**, so VMs can be added or removed without modifying NSG rules.
- ASGs make NSG rule management more scalable and easier to maintain in large environments.
- Example: You can create a rule that allows traffic from ASG **WebServers** to ASG **DatabaseServers** on port 1433 (SQL), instead of specifying IP addresses.
- [Application security groups](https://docs.azure.cn/en-us/virtual-network/application-security-groups)

##### 🛡️ Azure Firewall *(pricing required)*
- Azure Firewall is a cloud-native, managed network security service that protects Azure Virtual Network resources. Unlike NSGs or ASGs, which are rule-based and workload-specific, Azure Firewall is a **stateful, fully managed firewall** designed for enterprise-scale protection.
- Key features include:
  - Threat intelligence-based filtering (block known malicious IPs/domains).
  - Application and network-level filtering (control traffic by FQDNs, ports, protocols).
  - Web categories filtering (block or allow traffic based on content categories).
  - High availability and scalability (built-in, no need for manual configuration).
  - Centralized logging and monitoring (integrates with Azure Monitor and Sentinel).
- Azure Firewall is a **paid service**, with pricing based on tier (Basic, Standard, Premium) and data processing usage.
- [Deploy and configure Azure Firewall using the Azure portal](https://learn.microsoft.com/en-us/azure/firewall/tutorial-firewall-deploy-portal)

##### 🛡️ Resource Firewall
- A Resource Firewall in Azure refers to firewall rules applied directly at the **resource level**, rather than at the network level. This provides fine-grained control over which clients or services can access a specific Azure resource.
- Resource Firewalls are available for services such as **Azure Storage**, **Azure SQL Database**, and **Cosmos DB**.
- By default, most resource firewalls block all external traffic unless explicitly allowed.
- Rules can be based on **IP address ranges**, **Virtual Network integration**, or **Private Endpoints**, ensuring secure and restricted access.
- Example: Configure an IP network rule for Azure Storage to allow only trusted IP ranges.
- [Create an IP network rule for Azure Storage](https://learn.microsoft.com/en-us/azure/storage/common/storage-network-security-ip-address-range?tabs=azure-portal)

##### 🛡️ Application Gateway Firewall with Web Application Firewall (WAF) *(pricing required)*
- An Application Firewall in Azure is designed to protect web applications from common threats and vulnerabilities. The most widely used implementation is the **Azure Web Application Firewall (WAF)**, which operates at the application layer (HTTP/HTTPS traffic).
- WAF protects against **OWASP Top 10 vulnerabilities** such as SQL injection, cross-site scripting (XSS), and request forgery.
- It supports **custom rules** (IP, geolocation, request size, patterns) , **bot protectionF** and **footprinting** while allowing legitimate traffic.
- WAF integrates with **Azure Application Gateway**, **Azure Front Door**, and **Azure Content Delivery Network (CDN)** to provide flexible deployment options.
- Provides **centralized logging and monitoring** through Azure Monitor, Log Analytics, and Sentinel.
- WAF is a **paid feature**, with pricing based on the hosting service and traffic processed.
- [Create an application gateway with a Web Application Firewall using the Azure portal](https://learn.microsoft.com/en-us/azure/web-application-firewall/ag/application-gateway-web-application-firewall-portal)

##### 🛣️ Private Endpoint
- A Private Endpoint in Azure is a network interface that securely connects you to Azure services using a private IP address from your Virtual Network (VNet). This ensures traffic between your VNet and the Azure service travels entirely over the Microsoft backbone network, rather than the public internet.
- Private Endpoints are part of **Azure Private Link** and can be used with services such as **Azure Storage**, **Azure SQL Database**, **Cosmos DB**, and **Key Vault**.
- They help prevent **data exfiltration risks** by keeping traffic within Azure’s trusted network.
- Private Endpoints integrate with **Resource Firewalls** and **Private DNS zones** to provide fine-grained, secure, and seamless access to resources.
- [Create a private endpoint by using the Azure portal](https://learn.microsoft.com/en-us/azure/private-link/create-private-endpoint-portal?tabs=dynamic-ip)

##### 🌐 Azure Bastion *(pricing required)*
- Bastion is a fully managed PaaS service that provides secure RDP/SSH connectivity to VMs directly through the Azure portal.
- It eliminates the need to expose VMs to the public internet with open ports.
- Connections are tunneled over SSL, reducing attack surface.
- [Secure your Azure Bastion deployment](https://learn.microsoft.com/en-us/azure/bastion/secure-bastion)

##### 🛡️ Azure VPN Gateway *(pricing required)*
- Provides secure, encrypted connectivity between your on‑premises network and Azure Virtual Networks (VNets) over the public internet.
- [Create and manage a VPN gateway using the Azure portal](https://learn.microsoft.com/en-us/azure/vpn-gateway/tutorial-create-gateway-portal)

##### 🛣 Azure ExpressRoute *(pricing required)*
- Provides a private, dedicated connection between your on‑premises infrastructure and Microsoft cloud services (Azure, Microsoft 365, Dynamics 365).
- [Create and modify ExpressRoute circuits](https://learn.microsoft.com/en-us/azure/expressroute/expressroute-howto-circuit-portal-resource-manager)

### Recommendations for Azure Network Security
##### ☸ Hub-and-spoke Architecture
- Separates workloads into hub and spoke VNets for easier management.
- The hub VNet hosts shared services such as Azure Firewall, Bastion, and VPN Gateway.
- Spoke VNets contain application workloads (production, dev, test), isolated for security.
- Centralized routing through the hub ensures consistent inspection, governance, and compliance.
- Simplifies administration by isolating environments while maintaining secure connectivity.
- [Deploy Azure landing zones](https://learn.microsoft.com/en-us/azure/architecture/landing-zones/landing-zone-deploy)

##### 🌐 Subnet Segmentation
- Divide production and non-production subnets to reduce the attack surface.
- Apply network security groups (NSGs) and Azure Firewall rules to enforce segmentation.
- Prevent lateral movement of threats by restricting communication between sensitive workloads.
- Supports least privilege access and strengthens overall network defense.
- [Azure Virtual Network concepts and best practices](https://learn.microsoft.com/en-us/azure/virtual-network/concepts-and-best-practices#:~:text=In%20Azure%2C%20a%20subnet%20is%20a%20way,within%20subnets%20using%20Network%20Security%20Groups%20(NSGs).)

##### Azure DDoS Protection *(pricing required)*
- Definition: A managed service that protects Azure applications and resources from Distributed Denial of Service (DDoS) attacks, ensuring availability and resilience.
- Automatic Protection: Always‑on monitoring that detects and mitigates volumetric, protocol, and resource layer attacks without requiring workload changes.
- Adaptive Tuning: Learns traffic patterns for each protected resource and automatically adjusts thresholds to minimize false positives.
- Attack Analytics: Provides detailed telemetry, mitigation reports, and real‑time monitoring during and after attacks.
- Cost Protection: Helps safeguard against unexpected cloud usage charges caused by attack traffic.
- Integration: Works with Azure Monitor and Sentinel for alerts, logging, and incident response.
- Protection Modes
  - Network Protection:
    - Applied at the Virtual Network (VNet) level.
    - Protects all public IP addresses associated with resources in that VNet.
    - Best for scenarios where multiple workloads share the same VNet and need collective protection.
  - IP Protection:
    - Applied directly to individual public IP addresses.
    - Provides targeted protection for specific resources (e.g., a critical web app or API endpoint).
    - Best for workloads that require fine‑grained control or when only certain IPs need enhanced protection.
- [Create and configure Azure DDoS Network Protection using the Azure portal](https://learn.microsoft.com/en-us/azure/ddos-protection/manage-ddos-protection?tabs=new-vnet)
### Network Security Framework
