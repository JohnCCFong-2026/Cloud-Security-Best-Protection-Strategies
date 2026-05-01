# Security Fundamentals: Core Foundations - Network Security

## Getting started
For setup instructions, please follow the steps provided in AWS.

### Network Security
AWS network security is built on a shared responsibility model, where AWS secures the cloud infrastructure while you secure your workloads, identities, and data. Core protections include Virtual Private Cloud (VPC) isolation, firewalls, encryption, monitoring, and DDoS mitigation.

##### 🌐 Virtual Private Cloud (VPC)
- Provides logically isolated sections of the AWS cloud where you can launch resources.
- Example: You create a VPC with two subnets—one public for web servers and one private for databases. The public subnet connects to the internet via an Internet Gateway, while the private subnet only communicates internally.
- [Security best practices for your VPC](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-security-best-practices.html)

##### 🛡️ Security Groups
- Acts as a virtual firewall for EC2 instances, controlling inbound and outbound traffic.
- Example: You configure a security group to allow inbound HTTP (port 80) and HTTPS (port 443) traffic from anywhere, but restrict SSH (port 22) access to only your office IP address.
- [Control traffic to your AWS resources using security groups](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-security-groups.html)

##### 🚧 Network Access Control Lists (NACLs)
- Provides subnet-level traffic filtering with rules for inbound and outbound traffic.
- Example: You set a NACL to deny all traffic from a suspicious IP range while allowing normal traffic to your application subnet.
- [Control subnet traffic with network access control lists](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html)

##### 🌐 Amazon CloudFront
- A Content Delivery Network (CDN) that securely delivers websites, APIs, videos, and applications to users with low latency by caching content at AWS edge locations worldwide.
- Integrates with AWS WAF for application-layer protection and AWS Shield for DDoS mitigation, while supporting TLS/SSL encryption and access controls like signed URLs and cookies.
- Example: You host an e-commerce site with product images stored in S3. CloudFront caches these images at edge locations near your customers, ensuring fast page loads globally. At the same time, AWS WAF filters malicious requests (like SQL injection), and Shield Standard automatically mitigates DDoS attacks to keep your site available during peak shopping seasons.
- [Security in Amazon CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/security.html)

##### 🛡️ AWS WAF (Web Application Firewall)
- Protects web applications from common exploits (SQL injection, XSS, etc.).
- Works with CloudFront, Application Load Balancer (ALB), and API Gateway.
- Example: Block malicious requests while allowing legitimate traffic to your e-commerce site.
- [Security in your use of the AWS WAF service](https://docs.aws.amazon.com/waf/latest/developerguide/security.html)

##### 🛡️ AWS Network Firewall
- A managed firewall service for VPCs.
- Provides stateful inspection, intrusion prevention, and deep packet inspection.
- Example: Deploy in a centralized VPC to filter traffic across multiple subnets.
- [Security in your use of the AWS Network Firewall service](https://docs.aws.amazon.com/network-firewall/latest/developerguide/security.html)

##### 🛣️ AWS PrivateLink / VPC Endpoints
- Securely connect to AWS services without traversing the public internet.
- Example: Access S3 or DynamoDB privately from within your VPC.
- [Securely Access Services Over AWS PrivateLink](https://docs.aws.amazon.com/whitepapers/latest/aws-privatelink/aws-privatelink.html)

##### 🌐 AWS Bastion Host / Systems Manager Session Manager
- Provides secure administrative access to EC2 instances without exposing SSH ports.
- Example: Use Session Manager to connect to servers via the AWS console, eliminating the need for public IPs.
- [Access a bastion host by using Session Manager and Amazon EC2 Instance Connect](https://docs.aws.amazon.com/prescriptive-guidance/latest/patterns/access-a-bastion-host-by-using-session-manager-and-amazon-ec2-instance-connect.html)

##### ⚖️ Elastic Load Balancing (ELB)
- Distributes incoming traffic across multiple targets (EC2, containers, IPs) to ensure high availability and fault tolerance.
- Supports Application Load Balancer (ALB) for HTTP/HTTPS, Network Load Balancer (NLB) for TCP/UDP, and Gateway Load Balancer (GLB) for third‑party appliances.
- Example: Your web app runs on three EC2 instances in different Availability Zones. An ALB routes traffic evenly across them, while WAF filters malicious requests at the load balancer level.
- [Security in Elastic Load Balancing](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/security.html)

##### 🛣️ Amazon Route 53
- A highly available and scalable Domain Name System (DNS) web service that routes end‑user requests to AWS resources or external endpoints.
- Provides DNSSEC, health checks, and routing policies (weighted, latency‑based, geolocation) to improve security and performance.
- Example: You register example.com in Route 53 and configure it to route traffic to an Application Load Balancer. If one region becomes unhealthy, Route 53 automatically reroutes users to a healthy endpoint, ensuring availability.
- [Security in Amazon Route 53](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/security.html)

##### 🌐 Internet Gateway
- A horizontally scaled, redundant, and highly available VPC component that allows communication between resources in your VPC and the internet.
- Example: You attach an Internet Gateway to your VPC so that EC2 instances in a public subnet can serve web traffic to users on the internet.
- [Enable internet access for a VPC using an internet gateway](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Internet_Gateway.html)

##### 🌐 NAT Gateway
- Provides outbound internet access for resources in private subnets while preventing inbound connections from the internet.
- Example: Your database servers in a private subnet need to download OS updates. A NAT Gateway in the public subnet allows them to connect out securely without exposing them to inbound internet traffic.
- [NAT gateways](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html)

##### 🛣️ Transit Gateway
- A highly scalable hub that connects multiple VPCs and on‑premises networks through a central gateway.
- Simplifies network architecture by replacing complex peering relationships with a single managed service.
- Example: Your company has separate VPCs for production, development, and testing across multiple regions. A Transit Gateway connects them all securely, while also linking back to your on‑premises data center.
- [AWS Transit Gateway](https://docs.aws.amazon.com/whitepapers/latest/building-scalable-secure-multi-vpc-network-infrastructure/transit-gateway.html)

##### 🌐 VPC Peering
- A networking connection between two VPCs that enables routing traffic using private IPs. Traffic stays on the AWS backbone, not the public internet.
- Example: You connect a production VPC with a logging VPC so EC2 instances can send logs securely without exposing them to the internet.
- [Connect VPCs using VPC peering](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-peering.html)

##### 🌐 VPC Sharing
- Allows multiple AWS accounts to share subnets within a single VPC using AWS Resource Access Manager (RAM). This centralizes network management while enforcing consistent security policies.
- Example: A networking account owns the VPC, while application accounts (prod/dev/test) launch EC2 instances into shared subnets governed by the same firewall rules.
- [Share your VPC subnets with other accounts](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-sharing.html)

##### 🌐 AWS Cloud WAN
- A managed service to build a global wide area network across VPCs, branch offices, and data centers using AWS’s backbone.
- Example: A multinational company connects VPCs in Asia, Europe, and North America plus on‑prem offices into one Cloud WAN, applying consistent firewall and routing policies globally.
- [Quick start: Create an AWS Cloud WAN global network and core network](https://docs.aws.amazon.com/network-manager/latest/cloudwan/cloudwan-getting-started.html)

##### 🌐 Amazon VPC Lattice
- An application networking service that simplifies secure service‑to‑service communication across VPCs and accounts. Provides Zero Trust style authentication and authorization.
- Example: ECS services in one VPC securely call Lambda functions in another VPC, with VPC Lattice enforcing request‑level policies.
- [Security in Amazon VPC Lattice](https://docs.aws.amazon.com/vpc-lattice/latest/ug/security.html)

##### 🌐 AWS Direct Connect
- A dedicated, private network connection between your on‑premises environment (data center, office, or colocation facility) and AWS. It bypasses the public internet, providing lower latency, consistent performance, and enhanced security.
- Example: A financial services company sets up AWS Direct Connect from its colocation facility to the AWS Hong Kong Region. They create a private virtual interface to securely connect to their VPC for sensitive workloads, and a public virtual interface to access services like Amazon S3. This ensures trading applications have ultra‑low latency and secure connectivity without traversing the public internet.
- [Security in AWS Direct Connect](https://docs.aws.amazon.com/directconnect/latest/UserGuide/security.html)

### Recommendations for AWS Network Security
##### 🛡️ AWS Shield *(pricing required)*
- Protects against Distributed Denial of Service (DDoS) attacks.
- Versions:
  - Shield Standard → Free, automatically included with AWS services. Provides protection against common, most frequent network and transport layer DDoS attacks.
  - Shield Advanced (pricing required) → Paid tier with enhanced detection, mitigation, cost protection, and 24/7 support from the AWS DDoS Response Team (DRT).
- Example: Your e-commerce site uses AWS Shield Standard to automatically mitigate common DDoS attacks, ensuring availability during peak shopping seasons.
- [How AWS Shield and Shield Advanced work](https://docs.aws.amazon.com/waf/latest/developerguide/ddos-overview.html)

##### 🌐 Subnet Segmentation
- Subnet segmentation is the practice of dividing a VPC into multiple subnets to separate workloads by function, sensitivity, or trust level. This reduces the attack surface and limits lateral movement if one subnet is compromised.
- By segmenting workloads (e.g., web servers, application servers, databases), you enforce stricter access controls between tiers. This aligns with the principle of least privilege.
- Example:
  - Public subnet → hosts web servers accessible from the internet.
  - Private subnet → hosts application servers that only communicate with the web tier.
  - Isolated subnet → hosts databases with no direct internet access, only reachable from the application tier.
  - This segmentation ensures that even if the web tier is compromised, attackers cannot directly reach the databas

### Network Security Framework
##### Hub and Spoke with Organization
- This refers to a network architecture pattern where a central hub (often a Transit Gateway or a shared services VPC) connects multiple spoke VPCs or networks. It simplifies connectivity, centralizes security controls, and reduces complexity compared to full mesh peering.
- The hub acts as the central point for routing, inspection, and shared services (like logging, monitoring, or directory services).
- The spokes are individual VPCs (production, dev, test, etc.) that connect to the hub but not directly to each other.
- This enforces separation while still allowing controlled communication through the hub.
- Example:  
  - Your organization has:
    - A hub VPC with centralized firewalls, monitoring tools, and a Transit Gateway.
    - Spoke VPCs for production, development, and testing workloads.
    - Traffic between spokes flows through the hub, where it can be inspected and logged. This ensures consistent security policies across the organization.
- [REL02-BP04 Prefer hub-and-spoke topologies over many-to-many mesh](https://docs.aws.amazon.com/wellarchitected/latest/framework/rel_planning_network_topology_prefer_hub_and_spoke.html)
- [AWS Transit Gateway](https://docs.aws.amazon.com/whitepapers/latest/building-scalable-secure-multi-vpc-network-infrastructure/transit-gateway.html)
