# Security Fundamentals: Core Foundations - Network Security

## Getting started
For setup instructions, please follow the steps provided in AWS.

### Network Security
AWS network security is built on a shared responsibility model, where AWS secures the cloud infrastructure while you secure your workloads, identities, and data. Core protections include Virtual Private Cloud (VPC) isolation, firewalls, encryption, monitoring, and DDoS mitigation.

##### 🌐 Virtual Private Cloud (VPC)
- Provides logically isolated sections of the AWS cloud where you can launch resources.
- Example: You create a VPC with two subnets—one public for web servers and one private for databases. The public subnet connects to the internet via an Internet Gateway, while the private subnet only communicates internally.

##### 🛡️ Security Groups
- Acts as a virtual firewall for EC2 instances, controlling inbound and outbound traffic.
- Example: You configure a security group to allow inbound HTTP (port 80) and HTTPS (port 443) traffic from anywhere, but restrict SSH (port 22) access to only your office IP address.

##### 🚧 Network Access Control Lists (NACLs)
- Provides subnet-level traffic filtering with rules for inbound and outbound traffic.
- Example: You set a NACL to deny all traffic from a suspicious IP range while allowing normal traffic to your application subnet.

##### 🌐 Amazon CloudFront
- A Content Delivery Network (CDN) that securely delivers websites, APIs, videos, and applications to users with low latency by caching content at AWS edge locations worldwide.
- Integrates with AWS WAF for application-layer protection and AWS Shield for DDoS mitigation, while supporting TLS/SSL encryption and access controls like signed URLs and cookies.
- Example: You host an e-commerce site with product images stored in S3. CloudFront caches these images at edge locations near your customers, ensuring fast page loads globally. At the same time, AWS WAF filters malicious requests (like SQL injection), and Shield Standard automatically mitigates DDoS attacks to keep your site available during peak shopping seasons.

##### 🛡️ AWS WAF (Web Application Firewall)
- Protects web applications from common exploits (SQL injection, XSS, etc.).
- Works with CloudFront, Application Load Balancer (ALB), and API Gateway.
- Example: Block malicious requests while allowing legitimate traffic to your e-commerce site.

##### 🛡️ AWS Network Firewall
- A managed firewall service for VPCs.
- Provides stateful inspection, intrusion prevention, and deep packet inspection.
- Example: Deploy in a centralized VPC to filter traffic across multiple subnets.

##### 🛣️ AWS PrivateLink / VPC Endpoints
- Securely connect to AWS services without traversing the public internet.
- Example: Access S3 or DynamoDB privately from within your VPC.

##### 🌐 AWS Bastion Host / Systems Manager Session Manager
- Provides secure administrative access to EC2 instances without exposing SSH ports.
- Example: Use Session Manager to connect to servers via the AWS console, eliminating the need for public IPs.

##### ⚖️ Elastic Load Balancing (ELB)
- Distributes incoming traffic across multiple targets (EC2 instances, containers, IP addresses) to ensure high availability and fault tolerance.
- Provides automatic scaling and integrates with AWS Shield and AWS WAF for security at the edge.
- Supports TLS termination (offloading SSL/TLS encryption from your application servers) and can enforce security policies.
- Example: You deploy a web application across three EC2 instances in different Availability Zones. An Application Load Balancer (ALB) routes HTTP/HTTPS traffic evenly across them, while AWS WAF filters malicious requests at the load balancer level. If one instance fails, ELB automatically reroutes traffic to healthy targets, keeping your app available and secure.

##### 🛣️ Amazon Route 53
- A highly available and scalable Domain Name System (DNS) web service that routes end‑user requests to AWS resources or external endpoints.
- Provides DNSSEC, health checks, and routing policies (weighted, latency‑based, geolocation) to improve security and performance.
- Example: You register example.com in Route 53 and configure it to route traffic to an Application Load Balancer. If one region becomes unhealthy, Route 53 automatically reroutes users to a healthy endpoint, ensuring availability.

### Recommendations for AWS Network Security
##### 🛡️ AWS Shield *(pricing required)*
- Protects against Distributed Denial of Service (DDoS) attacks.
- Versions:
  - Shield Standard → Free, automatically included with AWS services. Provides protection against common, most frequent network and transport layer DDoS attacks.
  - Shield Advanced (pricing required) → Paid tier with enhanced detection, mitigation, cost protection, and 24/7 support from the AWS DDoS Response Team (DRT).
- Example: Your e-commerce site uses AWS Shield Standard to automatically mitigate common DDoS attacks, ensuring availability during peak shopping seasons.

### Network Security Framework
