# 🏰 Active Directory Mastery Roadmap

Welcome to your **playful yet detailed guide** to mastering **Active Directory (AD)**. This document is designed as your **single source of truth** 📖 to go from beginner ➝ expert ➝ master.

⏰ Includes timelines, 📚 concepts, 🛠️ labs, 🎯 milestones, and 🚀 mastery goals.

---

## 🎯 Why Master Active Directory?

Active Directory is the **core of Identity & Access Management (IAM)** in enterprise IT. It powers authentication, authorization, policies, and organizational structure. Mastering AD makes you:

- ✅ An IAM Specialist
- ✅ A Security Professional
- ✅ A Go-to person for Windows Infrastructure
- ✅ Well-prepared for IAM, IGA, Zero Trust, and Cybersecurity Architect roles

---

# 📆 Study Plan Timeline

Here’s a structured **12-week roadmap** (can be extended to 16 weeks with deeper labs).

| Week | Focus Area | Goal 🎯 |
|------|------------|--------|
| 1-2  | Fundamentals of AD | Understand basics, install AD DS |
| 3-4  | Core AD Components | Master domains, forests, trees, trusts |
| 5-6  | User & Group Management | Deep dive into accounts, policies, delegation |
| 7    | Group Policy Objects (GPO) | Design, apply, and troubleshoot GPOs |
| 8    | AD Infrastructure | FSMO, replication, schema, DNS, sites |
| 9    | Security & Delegation | Admin roles, least privilege, auditing |
| 10   | Advanced Features | RODC, ADFS, PKI integration, Azure AD Connect |
| 11   | AD Security Hardening | Zero Trust, PAM, MFA, Kerberos security |
| 12   | Real-World Labs | Troubleshooting, migration, DR scenarios |

---

# 🗝️ Core Concepts Breakdown

## 1️⃣ Fundamentals of Active Directory
- 🌐 **What is AD?**: Centralized identity & directory service
- 🖥️ **AD DS (Directory Services)**: The main role
- 🏗️ **Logical Structure**:
  - Forests 🌲
  - Trees 🌳
  - Domains 🏰
  - Organizational Units (OUs) 🗂️
- 📂 **Physical Structure**:
  - Domain Controllers (DCs)
  - Sites & Subnets
- 🧩 **Key Services**:
  - DNS integration
  - LDAP protocol
  - Kerberos authentication

⏳ *Timeline: Week 1-2*

🛠️ **Lab Ideas:**
- Install Windows Server + promote to DC
- Explore Active Directory Users and Computers (ADUC)

---

## 2️⃣ Domains, Trees, Forests, and Trusts
- 🏰 **Domain**: Core security boundary
- 🌲 **Tree**: Hierarchy of domains with a contiguous namespace
- 🌳 **Forest**: Collection of trees (top-level security boundary)
- 🤝 **Trust Relationships**:
  - One-way vs Two-way trusts
  - Forest trusts
  - External trusts
  - Shortcut trusts
  - Realm trusts

⏳ *Timeline: Week 3-4*

🛠️ **Lab Ideas:**
- Create child domain
- Configure trust between two forests

---

## 3️⃣ User, Groups & Computer Accounts
- 👩‍💻 **Users**: Properties, logon scripts, profiles
- 💻 **Computers**: Joining domain, secure channel
- 👥 **Groups**:
  - Security vs Distribution groups
  - Group scopes (Domain Local, Global, Universal)
- 🔁 **Group Nesting**: AGDLP, AGUDLP model
- ⚖️ **Delegation of Control**: Assign permissions to OUs

⏳ *Timeline: Week 5-6*

🛠️ **Lab Ideas:**
- Create users in bulk with PowerShell
- Delegate OU management to junior admin

---

## 4️⃣ Group Policy Objects (GPOs)
- 🎛️ **What is GPO?**: Centralized management of settings
- 📜 **GPO Types**:
  - Local GPO
  - Domain GPO
- 📌 **GPO Scope & Processing Order**:
  - Local → Site → Domain → OU
- ⚡ **Loopback Processing**
- 🛡️ **Security Filtering**
- 🧮 **WMI Filtering**
- 🕵️ **Troubleshooting Tools**:
  - gpresult
  - Group Policy Modeling

⏳ *Timeline: Week 7*

🛠️ **Lab Ideas:**
- Enforce password policy via GPO
- Deploy software via GPO

---

## 5️⃣ AD Infrastructure & Core Services
- 🏗️ **FSMO Roles**:
  - Schema Master
  - Domain Naming Master
  - RID Master
  - PDC Emulator
  - Infrastructure Master
- 🔄 **Replication**:
  - Intra-site vs Inter-site
  - AD replication topology
- 📂 **Schema**: Extending AD schema
- 🌍 **Sites & Subnets**: Improve replication and authentication
- 🧭 **DNS in AD**: Forward/reverse lookups, SRV records

⏳ *Timeline: Week 8*

🛠️ **Lab Ideas:**
- Transfer FSMO roles
- Simulate inter-site replication

---

## 6️⃣ Security, Delegation & Auditing
- 🛡️ **Admin Roles**: Enterprise Admins, Domain Admins, Schema Admins
- 🔑 **Least Privilege Principles**
- 🧾 **Auditing & Logging**: Track changes, login attempts
- 👮 **Account Policies**:
  - Password policies
  - Lockout policies
- 🕵️ **Monitoring Tools**: Event Viewer, Advanced Auditing

⏳ *Timeline: Week 9*

🛠️ **Lab Ideas:**
- Configure account lockout policy
- Enable auditing for AD object changes

---

## 7️⃣ Advanced Features
- 🧾 **Read-Only Domain Controller (RODC)**
- 🔐 **Active Directory Federation Services (ADFS)**
- 📜 **AD Certificate Services (AD CS)** & PKI integration
- ☁️ **Azure AD Connect & Hybrid Identity**
- 🛡️ **Fine-Grained Password Policies**
- 🔗 **Active Directory Lightweight Directory Services (AD LDS)**

⏳ *Timeline: Week 10*

🛠️ **Lab Ideas:**
- Deploy RODC in branch office
- Sync on-prem AD with Azure AD

---

## 8️⃣ AD Security & Hardening
- 🔑 **Kerberos & NTLM**: Authentication protocols
- 🛡️ **PAM (Privileged Access Management)**
- 🔐 **MFA integration**
- 🏰 **Zero Trust with AD**
- 📌 **Credential Guard, LAPS**
- 📊 **Security Baselines**

⏳ *Timeline: Week 11*

🛠️ **Lab Ideas:**
- Configure Kerberos delegation
- Implement Microsoft LAPS

---

## 9️⃣ Disaster Recovery & Migration
- 💾 **AD Backup & Restore**
- 🚨 **Authoritative vs Non-Authoritative Restore**
- 🔄 **AD Migration Tools (ADMT)**
- 🛠️ **Upgrade Domain Controllers**
- 🌐 **Cross-forest migrations**

⏳ *Timeline: Week 12*

🛠️ **Lab Ideas:**
- Perform authoritative restore of an OU
- Simulate DC failure and recovery

---

# 🧑‍💻 Tools & Skills to Learn Alongside
- 🐚 PowerShell for AD automation (Get-ADUser, Set-ADUser, etc.)
- 🔍 ADSI Edit
- 🛠️ Active Directory Administrative Center (ADAC)
- 📊 Monitoring with Event Viewer & Performance Monitor

---

# 🚀 Final Mastery Checklist
By the end, you should:

- ✅ Install & configure AD DS from scratch
- ✅ Manage users, groups, OUs, and policies confidently
- ✅ Understand domains, forests, trusts deeply
- ✅ Design & troubleshoot GPOs
- ✅ Control replication, FSMO roles, and schema
- ✅ Secure AD with auditing, delegation, and Zero Trust
- ✅ Implement advanced features like RODC, ADFS, and Azure AD Connect
- ✅ Perform backup, restore, and migrations
- ✅ Automate tasks using PowerShell

---

# 🎉 Gamification & Fun Goals
- 🎖️ Level 1: Deploy AD in your own lab
- 🎖️ Level 2: Master FSMO, Replication, GPOs
- 🎖️ Level 3: Secure AD with Zero Trust
- 🎖️ Level 4: Integrate with Azure AD
- 🎖️ Level 5: Troubleshoot & migrate like a Pro

---

# 📚 References & Resources
- Microsoft Learn (Active Directory Fundamentals)
- "Active Directory: Designing, Deploying, and Running Active Directory" by Brian Desmond
- PowerShell AD Cmdlets Reference
- Hands-on Practice in Virtual Labs

---

✨ With this single file, you have your **entire AD Mastery roadmap**. Stick to the timeline, do the labs, and soon you’ll be an **Active Directory Wizard 🧙‍♂️**!
