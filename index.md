
# Welcome to My Cyber Security Learning Journey

## Menu
- [💼 LinkedIn](https://www.linkedin.com/in/babatunde-armin-adesoye/) 
- [💻 Azure Security Labs](labs/) – Hands-on Azure Security labs mapped to CCSP domains.
- [🗺️ Roadmap](roadmap/) – My learning plan.
- [🤖 AI Security](ai_security/) – AI Security Thoughts and Notes.

## Me:

<img src="./general-media/profile-pic.png" alt="Profile Picture" width="300" height="450" style="border-radius:50%;" />



Hi, I’m **Tunde** 👋

I’m currently studying for the **Certified Cloud Security Professional (CCSP)** certification and building my skills in **Azure Security Engineering**.

This site is where I document my learning journey — from hands-on labs and technical notes to weekly reflections on what I’m learning and building along the way.

My goal is to move beyond theory and turn concepts into real, practical experience. To do that, I’ve created a learning roadmap that maps **CCSP domains** to **Azure Security Engineering labs**, allowing me to apply each idea in a real cloud environment as I progress.



| **CCSP Domain**                                  | **Focus Areas**                                                                                             | **AZ-500 Labs**                                                                          | **Hands-On Practice**                                                                                                          | **Evidence / Artifacts**                                                                                                  |
| :----------------------------------------------- | :---------------------------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------ |
| **D1. Cloud Concepts, Architecture & Design** ☁️ | Shared responsibility model<br>Secure reference architectures<br>IAM principles<br>Network segmentation     | RBAC<br>NSG / ASG<br>Azure Firewall 🔥                                                   | Map shared responsibility → RBAC 🛡️<br>Segment tiers with NSG/ASG 🌐<br>Control egress with Firewall 🔥                       | Architecture diagram 🏗️<br>Least-privilege RBAC matrix ✅<br>NSG/ASG ruleset excerpts 📄<br>Firewall rules + rationale 🔧 |
| **D2. Cloud Data Security** 🔒                   | Data classification<br>Encryption (rest / transit / use)<br>Key management & secrets<br>Data access control | Azure SQL security 🗄️<br>Service Endpoints 🔗<br>Azure Key Vault (Always Encrypted) 🗝️ | Enable storage encryption 🔑<br>Configure SAS/RBAC access 🧩<br>TDE + Always Encrypted 🔐<br>Restrict public access 🚫         | Encryption state screenshots 🔍<br>Key Vault policies 📜<br>Encrypted column configs 🗄️<br>Blocked public access test ❌  |
| **D3. Platform & Infrastructure Security** 🖥️   | Compute & network hardening<br>Container security 🐳<br>Isolation & connectivity                            | NSG / ASG 🌐<br>Azure Firewall 🔥<br>ACR & AKS security 🐳<br>JIT VM Access ⏱️           | Hub-and-spoke design 🏛️<br>Secure image pulls 🔐<br>Apply JIT access ⏱️<br>Private endpoints 🔗                               | Landing zone diagram 📊<br>ACR image scan reports 🛡️<br>AKS policy screenshots 🖼️<br>JIT audit logs 📑                  |
| **D4. Cloud Application Security** 🛠️           | Secure SDLC & DevSecOps 🔄<br>Containerized apps 🐳<br>Secrets & supply chain                               | ACR & AKS hardening 🐳                                                                   | Secure image lifecycle 🔐<br>Restrict pulls to approved registries ✅<br>Secretless workloads (AKV CSI / workload identity) 🗝️ | ACR signature logs 📋<br>AKS policy definitions 🚫<br>Workload identity demo 🎬                                           |
| **D5. Cloud Security Operations** 📡             | Monitoring & logging 📊<br>Threat detection 🕵️<br>Incident response 🚨                                     | Log Analytics 🛠️<br>Defender for Cloud 🛡️<br>JIT on VMs ⏱️<br>Microsoft Sentinel 🕵️   | Build DCR/DCE 🛠️<br>Enable Defender plans 🛡️<br>Create Sentinel analytics & automation 🤖                                    | KQL queries + rule JSON 📜<br>MITRE-mapped incidents 🗺️<br>Automation runbooks 🤖<br>Evidence pack 📦                    |
| **D6. Legal, Risk & Compliance** ⚖️              | ISO / NIST alignment 📚<br>Data residency 🌍<br>Policy & auditability                                       | Defender regulatory controls 🛡️<br>Key Vault encryption 🗝️                             | Map workloads to standards 📌<br>Assess compliance posture 📈<br>Document key custody decisions 🔑                             | Compliance dashboard 📊<br>POA&M remediation list 📝<br>Key management decision record 🔐                                 |




