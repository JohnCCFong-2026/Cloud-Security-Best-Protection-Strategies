# Security Fundamentals: Core Foundations - Application Security

## Getting started
For setup instructions, please follow the steps provided in AWS.

### Application Security
AWS application security centers on safeguarding workloads and code execution across their lifecycle from development to deployment and runtime through layered defenses. Core measures include secure identity and access controls, hardened network boundaries, encryption of sensitive data, automated vulnerability scanning, runtime protection with web application firewalls, and continuous monitoring with threat detection services.

##### 👥 AWS Identity and Access Management (IAM)
- Provides fine‑grained access control to AWS resources, enforcing least privilege.
- Example: Restricting access so only specific IAM roles can deploy code, while customer data remains inaccessible to developers.

##### 🔑 AWS Secrets Manager
- Securely stores and rotates credentials, API keys, and database passwords.
- Example: A web application retrieves database credentials from Secrets Manager at runtime instead of hardcoding them in source code.
- [Security in AWS Secrets Manager](https://docs.aws.amazon.com/secretsmanager/latest/userguide/security.html)

##### 🛡️ AWS Web Application Firewall (WAF)
- Protects applications from common exploits such as SQL injection, cross‑site scripting (XSS), and bot traffic.
- Example: An e‑commerce site uses WAF rules to block malicious requests targeting its checkout page.

##### 🧪 Secure Development Lifecycle
- Integrate security checks into CI/CD pipelines with CodePipeline and Inspector.
- Example: A fintech company runs automated scans during build stages to catch insecure dependencies before release.
- [Application security](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/application-security.html)

##### 🔒 Encryption in Transit
- Enforce TLS 1.2+ for all application traffic and API calls.
- Example: A healthcare app secures patient data transmitted between its web front‑end and RDS database using TLS.

##### 📦 Dependency Scanning (via Amazon Inspector + CodePipeline)
- Checks third‑party libraries and packages for known vulnerabilities.
- Example: Inspector flags an outdated open‑source package with a critical CVE; developers update the dependency before deployment.

##### 🔗 AWS API Gateway (API Security)
- Secures APIs by enforcing authentication, authorization, throttling, and monitoring.
- Example: A company exposes a customer API through API Gateway. Requests must include a valid IAM or Cognito token, and rate limits prevent denial‑of‑service attacks.

##### ⚙️ Amazon Inspector (Application Security)
- Amazon Inspector also secures application workloads by scanning Lambda functions and container images (ECS/EKS). It analyzes code packages and dependencies for insecure libraries or misconfigurations.
- This ensures applications don’t ship with vulnerable components.
- Example (Lambda): A serverless function uses an outdated Node.js library with a critical CVE. Inspector flags the issue, and developers update the dependency before redeployment.
- Example (Containers): An e‑commerce API container image includes a vulnerable version of log4j. Inspector detects the CVE during the build process, and the CI/CD pipeline blocks deployment until the image is rebuilt with a patched version.
- [Amazon Inspector Code Security](https://docs.aws.amazon.com/inspector/latest/user/code-security-assessments.html)

##### 🛡️ AWS Shield
- Provides managed Distributed Denial of Service (DDoS) protection at both the network and application layers.
- Two tiers:
  - Shield Standard (included by default) protects against common network and transport layer DDoS attacks.
  - Shield Advanced offers enhanced detection, mitigation, cost protection, and 24/7 access to the AWS DDoS Response Team (DRT).
- Helps ensure that applications remain available and resilient even under large-scale attack attempts.
- Example: A media streaming service uses AWS Shield Advanced to automatically mitigate volumetric DDoS attacks targeting its video delivery endpoints, ensuring uninterrupted streaming for customers.

### Recommendations for AWS Application Security
##### 🧩 Static Application Security Testing (SAST)
- Analyzes source code and binaries before deployment to detect vulnerabilities early in the development cycle.
- Example: Running SAST scans in CodeBuild to identify insecure coding patterns (like hardcoded credentials) before merging into production.
- [[QA.ST.4] Enhance source code security with static application security testing](https://docs.aws.amazon.com/wellarchitected/latest/devops-guidance/qa.st.4-enhance-source-code-security-with-static-application-security-testing.html)

##### ⚡ Dynamic Application Security Testing (DAST)
- Tests running applications by simulating real‑world attacks to uncover runtime vulnerabilities.
- Example: Using DAST tools integrated with AWS environments to detect SQL injection or XSS vulnerabilities in a staging web app before release.
- [[QA.ST.5] Evaluate runtime security with dynamic application security testing](https://docs.aws.amazon.com/wellarchitected/latest/devops-guidance/qa.st.5-evaluate-runtime-security-with-dynamic-application-security-testing.html)

### Applicaton Security Framework
##### 🔄 AWS DevSecOps
- Integrates security into every stage of the software lifecycle (plan → code → build → test → release → deploy → operate → monitor).
- Ensures that applications are secure by design, continuously tested, and monitored in production.
- Core practices include shift‑left security, automated compliance checks, immutable infrastructure, runtime protection, and continuous monitoring.
- Example: A fintech company uses CodeBuild for SAST scans, Amazon Inspector for container vulnerability checks, AWS WAF for runtime protection, and GuardDuty for anomaly detection. If GuardDuty flags suspicious API calls, a Lambda function automatically quarantines the compromised resource.
