# 🛠️ Group Policy Objects (GPO) in Active Directory

Group Policy is a core feature of **Active Directory (AD)** that allows administrators to **centrally manage and configure operating systems, applications, and user settings** in an Active Directory environment.  

---

## 📌 What is a GPO?
- A **Group Policy Object (GPO)** is a collection of settings that control the working environment of users and computers.  
- It applies policies like password rules, software installations, desktop restrictions, and security configurations.  
- GPOs are stored in **Group Policy Container (GPC)** in AD and **Group Policy Template (GPT)** in SYSVOL.

---

## 🔑 Components of GPO
1. **Group Policy Container (GPC)**  
   - Stored in **Active Directory** (within the domain partition).  
   - Contains version information and GPO attributes.  

2. **Group Policy Template (GPT)**  
   - Stored in the **SYSVOL folder** on each Domain Controller.  
   - Contains actual policy settings like scripts, software packages, security templates.  

---

## 📍 GPO Scope of Application
Group Policies are applied in the following **order of precedence** (from lowest to highest):  

1. **Local Policy** (applies to single computer only).  
2. **Site-level GPOs**.  
3. **Domain-level GPOs**.  
4. **Organizational Unit (OU) GPOs** (highest priority).  

👉 If multiple policies conflict, the **last applied GPO** (closest to the object) wins.

---

## 🧩 Types of GPO
1. **Local GPO**  
   - Exists on a single computer.  
   - Cannot be centrally managed.  

2. **Non-local (AD-based) GPO**  
   - Linked to **Sites, Domains, or OUs**.  
   - Centrally managed by domain admins.  

---

## ⚙️ Common Use Cases of GPO
- Enforce **password policies** (complexity, expiration, lockout).  
- Deploy and configure **software applications**.  
- Restrict **USB drives or CD-ROM access**.  
- Configure **firewall and security settings**.  
- Set **logon/logoff or startup/shutdown scripts**.  
- Redirect folders (e.g., Documents, Desktop).  

---

## 🔗 Linking GPOs
- GPOs do not apply unless **linked** to a **Site, Domain, or OU**.  
- One GPO can be linked to multiple OUs.  
- One OU can have multiple GPOs.  

---

## 🚦 GPO Processing Order
GPOs process in the order:  
**Local → Site → Domain → OU (LSDOU rule)**  

Example:  
- A user belongs to an OU where a "No USB Access" GPO is applied.  
- The Domain has a "Password Expiry 90 Days" GPO.  
- Result: Both policies apply → User cannot use USB, and password expires every 90 days.  

---

## 🧮 GPO Filtering
- **Security Filtering** → Apply GPO only to specific groups/users.  
- **WMI Filtering** → Apply GPO based on conditions (e.g., OS version, laptop vs desktop).  

---

## 🔒 Security & Best Practices
- Use **OU-based GPOs** for fine-grained control.  
- Avoid over-linking GPOs at the domain level (impacts all users/computers).  
- Test policies in a **staging OU** before applying to production.  
- Enable **Group Policy Loopback Processing** for applying user policies on specific computers (e.g., kiosk systems).  

---

## 📂 GPO Storage Locations
- **GPC (in AD)**: Holds version & metadata.  
- **GPT (in SYSVOL)**: Holds actual policy files.  

# 🛠️ Group Policy Objects (GPO) – Complete Breakdown

Group Policy is the backbone of centralized management in **Active Directory (AD)**.  
Below are the **11 key areas** you must know to master GPOs. 🚀

---

## 1. 📍 Scope of GPO Application (LSDOU)

Group Policies follow the **LSDOU order**:  
1. **Local** – Policies on the individual machine.  
2. **Site** – Policies applied to an AD Site.  
3. **Domain** – Policies applied to the whole domain.  
4. **Organizational Unit (OU)** – Policies applied to specific users/computers.  

👉 If conflicts exist, the **last applied (OU)** takes precedence.

---

## 2. 🧩 Types of GPO

- **Local GPO**  
  Exists only on one computer, useful in standalone environments.  

- **Domain GPO**  
  Applied at **Site, Domain, or OU** level, managed via **Group Policy Management Console (GPMC)**.  

---

## 3. ⚙️ What Can a GPO Do?

- **Security Settings** → Password length, lockout, Kerberos.  
- **Software Deployment** → Install/update applications automatically.  
- **Device Restrictions** → Disable USB, printers, removable drives.  
- **Scripts** → Run logon/logoff or startup/shutdown scripts.  
- **Folder Redirection** → Move Documents/Desktop to file server.  
- **Network Configurations** → Proxy settings, firewall rules, mapped drives.  

---

## 4. 🔗 Linking GPOs

- A GPO **must be linked** to Site, Domain, or OU to apply.  
- One GPO can be linked to multiple OUs.  
- One OU can have multiple GPOs.  
- **Link order** decides which one wins in conflicts.  

---

## 5. 🚦 GPO Processing Order

1. Local Policies  
2. Site GPOs  
3. Domain GPOs  
4. OU GPOs  

👉 Example:  
- OU-level GPO disables USB.  
- Domain-level GPO enables USB.  
- Result → **OU policy wins**.  

---

## 6. 🧮 GPO Filtering

- **Security Filtering** → Apply GPO to selected users/groups.  
- **WMI Filtering** → Apply based on machine properties (e.g., only laptops, only Windows 11).  

---

## 7. 🔒 Best Practices

- Use **Domain-level GPOs** for broad security rules.  
- Use **OU-level GPOs** for fine-grained rules.  
- Avoid linking too many GPOs at the **root Domain**.  
- Test in **staging OUs** first.  
- Use **Loopback Processing** for kiosks, labs, and shared PCs.  

---

## 8. 📂 Storage Locations

- **GPC (Group Policy Container)** → Stored in AD, keeps metadata & version info.  
- **GPT (Group Policy Template)** → Stored in SYSVOL, keeps actual files/settings.  

---

## 9. 🔍 Real-World Example (Contoso Ltd.)

- **Security GPO (Domain)**  
  - Password length = 12 chars  
  - Lockout after 5 failed attempts  
  - Disable anonymous access  

- **Workstation GPO (OU)**  
  - Block USB  
  - Deploy Chrome & Teams  
  - Redirect Documents  

- **Kiosk GPO (OU + Loopback)**  
  - Only POS app allowed  
  - Block Task Manager  

👉 Result:  
- Everyone follows Domain-level security.  
- Employees get workstation rules.  
- Kiosks are locked down.  

---

## 10. 📊 Management Tools

- **GPMC** → Manage domain GPOs.  
- **gpedit.msc** → Local GPO editor.  
- **gpupdate /force** → Force-refresh policies.  
- **rsop.msc** → Check effective applied policies.  

---

## 11. 📝 Summary

- GPO = Core AD management tool.  
- Stored in **GPC (AD)** + **GPT (SYSVOL)**.  
- Applied in **LSDOU order**.  
- Supports **filtering & loopback**.  
- Powers **security, deployment, and standardization** in enterprises.  

---
