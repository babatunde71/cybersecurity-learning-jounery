
# Welcome to My Cyber Security Learning Journey

## Menu
- [💼 LinkedIn](https://www.linkedin.com/in/babatunde-adesoye-0b1b6b1b1/) 
- [💻 Azure Security Labs](labs/) – Hands-on Azure Security labs mapped to CCSP domains.
- [🗺️ Roadmap](roadmap/) – My learning plan.


![Profile Picture](./general-media/profile-pic.png)



Hi, I’m **Tunde** 👋

I’m currently studying for the **Certified Cloud Security Professional (CCSP)** certification and building my skills in **Azure Security Engineering**.

This site is where I document my learning journey — from hands-on labs and technical notes to weekly reflections on what I’m learning and building along the way.

My goal is to move beyond theory and turn concepts into real, practical experience. To do that, I’ve created a learning roadmap that maps **CCSP domains** to **Azure Security Engineering labs**, allowing me to apply each idea in a real cloud environment as I progress.



| CCSP Domain | Focus Areas | AZ-500 Applied Skills (Microsoft Learn) | AZ-500 GitHub Labs | Hands-On Skills to Practice | Evidence / Artifacts |
|------------|------------|----------------------------------------|------------------|----------------------------|-------------------|
| **D1. Cloud Concepts, Architecture & Design** ☁️ | - Shared responsibility model<br>- Secure reference architectures<br>- IAM principles<br>- Network segmentation | Get started with cloud security & monitoring tasks | - 01 – Role-Based Access Control (RBAC)<br>- 02 – Network Security Groups (NSG) & Application Security Groups (ASG)<br>- 03 – Azure Firewall | - Map shared responsibility into RBAC assignments 🛡️<br>- Segment tiers with NSG/ASG 🌐<br>- Control egress with Azure Firewall 🔥 | - Architecture diagram 🏗️<br>- Least-privilege RBAC matrix ✅<br>- NSG/ASG ruleset excerpts 📄<br>- Firewall rules with rationale 🔧 |
| **D2. Cloud Data Security** 🔒 | - Data classification<br>- Encryption (at rest/in transit/in use)<br>- Key management & secrets handling<br>- Data access control | Secure storage for Azure Files & Blob Storage | - 05 – Securing Azure SQL Database<br>- 06 – Service Endpoints & Securing Storage<br>- 07 – Azure Key Vault (Always Encrypted) | - Enable storage encryption 🔑<br>- Configure SAS/RBAC access 🧩<br>- SQL TDE & Always Encrypted with AKV 🗝️<br>- Restrict public access 🚫 | - Encryption state screenshots 🔍<br>- Key Vault access policies 📜<br>- Always Encrypted column settings 🗄️<br>- Blocked public access test results ❌ |
| **D3. Cloud Platform & Infrastructure Security** 🖥️ | - Compute & network hardening<br>- Container security<br>- Isolation & secure connectivity | Configure secure access to workloads using Azure networking | - 02 – NSG/ASG<br>- 03 – Azure Firewall<br>- 04 – Securing ACR & AKS<br>- 10 – Just-In-Time (JIT) VM Access | - Design hub-and-spoke / landing zone controls 🏛️<br>- Secure container images & pull restrictions 🐳<br>- Apply JIT VM access ⏱️<br>- Service endpoints & private links 🔗 | - Landing-zone diagram 📊<br>- ACR image scan reports 🛡️<br>- AKS policy/admission screenshots 🖼️<br>- JIT request & audit logs 📑 |
| **D4. Cloud Application Security** 🛠️ | - Secure SDLC & DevSecOps<br>- Containerized apps<br>- Secrets & supply chain management | — | - 04 – Securing ACR & AKS (RBAC reused for pipelines) | - Secure container image lifecycle 🔐<br>- Restrict pulls to approved registries ✅<br>- Secretless workloads using AKV CSI / workload identity 🗝️ | - ACR content trust & signature logs 📋<br>- AKS policy definitions (e.g., no `:latest`) 🚫<br>- Workload identity / secretless demo 🎬 |
| **D5. Cloud Security Operations** 📡 | - Monitoring & logging<br>- Threat detection<br>- Incident response | Deploy & configure Azure Monitor | - 08 – Log Analytics, Storage & DCR<br>- 09 – Defender for Cloud Enhanced Security<br>- 10 – JIT on VMs<br>- 11 – Microsoft Sentinel | - Build Log Analytics workspace & DCR/DCE 🛠️<br>- Enable Defender plans & regulatory initiatives 🛡️<br>- Create Sentinel analytics, hunting queries & automation 🕵️ | - KQL queries & rule JSON 📜<br>- Incidents triaged with MITRE mapping 🗺️<br>- Automation runbooks executed 🤖<br>- Sentinel/Defender evidence pack 📦 |
| **D6. Legal, Risk & Compliance** ⚖️ | - Framework alignment (ISO/NIST/UK NCSC)<br>- Data residency<br>- Policy enforcement & auditability | Secure Azure services using Defender for Cloud regulatory controls | - 09 – Defender for Cloud Enhanced Security<br>- 07 – Key Vault (Always Encrypted) | - Map workloads to compliance standards 📌<br>- Assess compliance posture 📈<br>- Document encryption & key custody decisions 🗝️ | - Regulatory compliance dashboard before/after 📊<br>- POA&M item list with remediation actions 📝<br>- Key management decision record 🔑 |




