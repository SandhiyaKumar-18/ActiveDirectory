# 🏗️ Active Directory Structure & Key Services

Active Directory (AD) has two sides:  
- 🏗️ **Logical Structure** → How objects are organized.  
- 📂 **Physical Structure** → How it’s implemented on servers & networks.  
- 🧩 **Key Services** → Protocols and integrations that make it all work.  

---

## 🏗️ Logical Structure

Logical = **How you organize things in AD for management** (like folders & hierarchy).

### 🌲 Forests
- The **top-most container** in AD.
- Represents the **security boundary** — trust doesn’t automatically extend beyond a forest.
- Contains one or more **trees**.

### 🌳 Trees
- A **collection of domains** that share a **common namespace** (like `company.com`, `hr.company.com`).
- Domains in a tree are automatically connected with **two-way transitive trust**.

### 🏰 Domains
- The **core unit** of AD structure.
- Holds **users, groups, computers, and policies**.
- Each domain has its own **security policies & authentication**.
- Example: `sales.company.com`.

### 🗂️ Organizational Units (OUs)
- Containers inside domains used to **group objects** (users, computers, groups).
- Allow **delegation of admin rights** (e.g., HR manages only their OU).
- Group Policy Objects (GPOs) can be applied at the OU level.

---

## 📂 Physical Structure

Physical = **How AD is actually implemented on servers & networks.**

### 🖥️ Domain Controllers (DCs)
- Servers that **run AD DS**.
- Store the **AD database (NTDS.dit)**.
- Handle **authentication & replication**.

### 🌐 Sites & Subnets
- Represent the **physical network topology**.
- **Sites** = Groups of DCs in the same network location.  
- **Subnets** = Define IP ranges for mapping clients to sites.
- Helps optimize **replication & authentication traffic**.

---

## 🧩 Key Services

AD wouldn’t work without its underlying services:

### 🌍 DNS Integration
- AD is tightly integrated with **DNS**.
- Domain Controllers register SRV records in DNS so clients can find them.
- Example: `ldap._tcp.dc._msdcs.company.com`.

### 📡 LDAP Protocol
- **Lightweight Directory Access Protocol**.
- Standard protocol for querying and modifying directory services.
- Example: `ldap://dc1.company.com`.

### 🔑 Kerberos Authentication
- Default **authentication protocol** in AD.
- Provides **secure, ticket-based authentication**.
- Prevents sending passwords over the network.

---

## 🎯 Summary

- **Logical structure** organizes objects (forests, trees, domains, OUs).  
- **Physical structure** maps AD to real servers & networks (DCs, sites, subnets).  
- **Key services** (DNS, LDAP, Kerberos) make the whole system function.  

