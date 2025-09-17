# 🖥️ Domain Controllers (DCs) in Active Directory

A **Domain Controller (DC)** is the **backbone of Active Directory** 💪.  
It’s a **server that runs AD DS** and is responsible for **authentication, authorization, policy enforcement, and replication** across the domain.

---

## 🔑 Core Responsibilities

### 1. 🛂 Authentication
- Verifies **usernames and passwords** when someone logs in.  
- Uses **Kerberos (default)** or **NTLM (legacy)** protocols.  

### 2. 🗝️ Authorization
- Decides **what resources a user can access** (files, printers, apps).  
- Example:  
  - Alice (HR) → Can access `HR Share`.  
  - Bob (IT) → Can access `Servers OU`.  

### 3. 📚 Directory Database
- Stores the **Active Directory database (`NTDS.dit`)**.  
- Contains all objects:
  - Users 👩‍💻
  - Groups 👥
  - Computers 💻
  - Printers 🖨️
  - Policies 📜  

### 4. 🔄 Replication
- Synchronizes AD changes between **multiple DCs**.  
- Ensures **consistency across the domain**.  
- Example: Password reset in New York → replicated to London DC.  

### 5. 🛡️ Policy Enforcement
- Applies **Group Policy Objects (GPOs)** to users & computers.  
- Examples:  
  - Enforce strong passwords.  
  - Disable USB drives.  
  - Configure desktop backgrounds.  

---

## 📂 Types of Domain Controllers

### 🔹 Writable DC
- Standard DC with **read/write access**.  
- You can create users, reset passwords, modify groups, etc.  

### 🔹 Read-Only DC (RODC)
- Holds a **read-only copy** of the AD database.  
- Ideal for **branch offices** with lower security.  
- Prevents attackers from making changes if compromised.  
- Can be configured to **cache specific credentials only**.  

---

## ⚙️ FSMO Roles (Flexible Single Master Operations)

Even though AD supports **multi-master replication**, some tasks need a **single master**.  
That’s where FSMO roles come in.  

There are **5 FSMO roles**:  

### Domain-Level FSMO Roles
1. **RID Master** 🆔 – Issues unique IDs for new objects.  
2. **PDC Emulator** ⏰ – Handles time sync, password changes, legacy NT4 logins.  
3. **Infrastructure Master** 🏗️ – Updates references to objects in other domains.  

### Forest-Level FSMO Roles
4. **Schema Master** 📖 – Manages schema changes (e.g., add new attributes).  
5. **Domain Naming Master** 🌍 – Manages domain additions/removals in the forest.  

---

## 🔄 Replication in Detail

- **Intra-Site Replication** (within same site):  
  - Fast, uncompressed, frequent.  
- **Inter-Site Replication** (between sites):  
  - Compressed, scheduled, optimized for WAN links.  

⚡ This ensures **all DCs have the same view of AD objects**.  

---

## 🧩 Best Practices for DCs

- Always deploy **at least 2 DCs per domain** (redundancy).  
- Use **RODCs** for branch offices.  
- Enable **backups** of the AD database regularly.  
- Place DCs in **secure locations** (physically and network-wise).  
- Use **separate sites and subnets** for optimal replication.  

---

## 🎯 Simple Analogy

Think of a **Domain Controller** as a **super security officer in a company HQ** 🏢:

- 🛂 Checks ID cards at the door (authentication).  
- 🗝️ Decides which rooms you can enter (authorization).  
- 📚 Maintains the employee directory (AD database).  
- 🔄 Calls other HQs to sync updates (replication).  
- 🛡️ Enforces company rules (Group Policy).  

---

## ✅ Summary

- A **DC runs AD DS** and handles **auth, authZ, replication, and policies**.  
- Types: **Writable DC** & **RODC**.  
- **FSMO roles** ensure unique, forest-wide consistency.  
- Replication keeps all DCs in sync.  
- Redundancy + security = **healthy AD environment**.  

---
