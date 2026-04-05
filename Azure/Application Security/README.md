# Security Fundamentals: Core Foundations - Application Security

## Getting started
For setup instructions, please follow the steps provided in Azure.

### Application Security
Azure application security focuses on protecting the applications, APIs, and code that run on the cloud platform. The goal is to ensure that applications are securely developed, deployed, and operated, with strong identity integration, encrypted communication, and safe handling of secrets.

##### 🔒 SSL/TLS Certificates (Secure Communication)
- Azure enforces encrypted communication between clients and applications using SSL/TLS. Certificates can be managed through Azure Key Vault for automated rotation and renewal, ensuring that sensitive data in transit is protected.
- Example: A web app hosted on Azure App Service binds an SSL certificate to its domain. All customer traffic (https://myshop.com) is encrypted, preventing attackers from intercepting login credentials or payment details.
- [Use a custom domain and a managed certificate to secure your app](https://learn.microsoft.com/en-us/azure/app-service/tutorial-secure-domain-certificate)

##### 👤 Microsoft Entra ID (Identity & Access Integration)
- Microsoft Entra ID provides centralized identity management for applications. It supports Single Sign-On (SSO), Multi-Factor Authentication (MFA), and modern protocols like OAuth2 and OpenID Connect. Applications can also use managed identities to securely access Azure resources without storing credentials in code.
- Example: An internal HR portal uses Azure AD for authentication. Employees log in with their corporate accounts, and conditional access policies enforce MFA when logging in from outside the office network.

##### ⚙️ Secure Deployment of Code (DevSecOps)
- Azure integrates security into the application lifecycle through CI/CD pipelines. Tools like Azure DevOps and GitHub Actions can run automated security scans, while Microsoft Defender for DevOps checks for vulnerabilities in code and dependencies. Infrastructure as Code templates can be validated against security policies, and container workloads in Azure Kubernetes Service (AKS) can be scanned for misconfigurations.
- Example: A developer pushes new code to GitHub. The CI/CD pipeline runs automated scans for exposed secrets or outdated libraries. Only after passing these checks is the code deployed to Azure App Service, ensuring secure delivery.
- [DevSecOps for infrastructure as code (IaC)](https://learn.microsoft.com/en-us/azure/architecture/guide/devsecops/devsecops-on-aks)

### Recommendations for Azure Application Security
##### 🛠️ Microsoft Defender for DevOps (pricing required)
- Defender for DevOps integrates security into your CI/CD pipelines. It scans source code, dependencies, and infrastructure templates for vulnerabilities before deployment. This helps prevent insecure code from reaching production.
- Example: A developer commits code to GitHub. Defender for DevOps automatically scans the repository, detects a vulnerable library, and alerts the team. The pipeline blocks deployment until the issue is fixed, ensuring only secure code is released to Azure.

##### 🔑 Azure Key Vault
- Key Vault securely stores and manages secrets, certificates, and encryption keys. It prevents developers from hardcoding sensitive information in applications and supports automated rotation of credentials.
- Example: An application needs a database connection string. Instead of embedding it in code, the app retrieves the secret from Azure Key Vault at runtime. This keeps credentials safe and reduces the risk of accidental exposure.

##### 🛡️ Web Application Firewall (WAF)
- WAF protects applications from common web-based attacks such as SQL injection, cross-site scripting (XSS), and malicious bots. It can be deployed with Azure Front Door or Application Gateway.
- Example: A public-facing e-commerce site uses Azure WAF. When an attacker attempts a SQL injection in the login form, WAF blocks the malicious request before it reaches the application, keeping customer data secure.

##### 📈 Continuous Monitoring (Microsoft Defender for Cloud)
- Defender for Cloud continuously monitors applications, workloads, and configurations. It detects vulnerabilities, misconfigurations, and suspicious activity, providing security recommendations and alerts.
- Example: A company hosts multiple APIs in Azure. Defender for Cloud detects that one API endpoint is exposed without authentication. It alerts the security team and recommends enabling Azure AD authentication, preventing unauthorized access.

##### 🧩 SAST (Static Application Security Testing)
- SAST analyzes source code or binaries during development to detect vulnerabilities before deployment. It helps developers fix issues early in the lifecycle.
- Example: A CI/CD pipeline runs a SAST tool on a developer’s code and finds hardcoded credentials in a configuration file. The build fails, and the developer removes the secret, ensuring it is stored securely in Azure Key Vault instead.

##### 🧪 DAST (Dynamic Application Security Testing)
- DAST tests running applications by simulating real-world attacks. It identifies vulnerabilities in the application’s runtime behavior, such as input validation flaws.
- Example: A QA team runs a DAST scan against a staging environment of a web app. The tool detects that the login form is vulnerable to cross-site scripting (XSS). The issue is fixed before the app is deployed to production in Azure.

##### 📦 Dependency Scanning
- Dependency scanning checks third-party libraries and packages for known vulnerabilities. This prevents insecure components from being included in applications.
- Example: Defender for DevOps flags an outdated open-source package with a critical CVE. Developers update the dependency before deployment, reducing risk.

##### 🔗 Azure API Management (API Security)
- API Management secures APIs by enforcing authentication, authorization, throttling, and monitoring. It helps prevent abuse and ensures only trusted clients can access APIs.
- Example: A company exposes a customer API through API Management. Requests must include a valid Azure AD token, and rate limits prevent denial-of-service attacks.

### Applicaiotn Security Framework
##### 🛡️ OWASP Application Security Framework
- Focuses on the OWASP Top 10 vulnerabilities (SQL injection, XSS, insecure deserialization, etc.).
- Recommends practices like SAST and DAST to detect and mitigate these risks.
- Example: Running SAST in CI/CD to catch hardcoded secrets, and DAST scans to block XSS in a login form.

##### 🏗️ Microsoft Secure Development Lifecycle (SDL)
- Microsoft’s own framework for secure application development.
- Encourages integrating SAST/DAST into DevOps pipelines, threat modeling, and secure coding practices.
- Example: An Azure DevOps pipeline includes SDL practices — automated SAST scans, dependency checks, and security gates before deployment.

##### 🏛️ NIST Cybersecurity Framework (CSF)
- A broader security framework that includes application security as part of “Protect” and “Detect” functions.
- Example: Using Defender for Cloud for continuous monitoring (Detect) and Key Vault for secret management (Protect).
