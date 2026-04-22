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

### Recommendations for AWS Network Security
##### 🛡️ AWS Shield *(pricing required)*
- Protects against Distributed Denial of Service (DDoS) attacks.
- Example: Your e-commerce site uses AWS Shield Standard to automatically mitigate common DDoS attacks, ensuring availability during peak shopping seasons.
