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

# 🏗️ Active Directory Logical Structure (Deep Dive)

The **Logical Structure** of Active Directory defines **how objects (users, groups, computers, printers, etc.) are organized and managed**.  
Think of it like the **blueprint of a city** 🏙️, where every building and road has a purpose.

Logical structure has **four main components**:  
🌲 Forests → 🌳 Trees → 🏰 Domains → 🗂️ OUs  

---

## 🌲 Forests

- The **highest-level container** in Active Directory.  
- A forest is a **security boundary**:  
  - **Admins in one forest cannot control another forest** (unless explicit trust is created).  
- It contains:  
  - One or more **trees** 🌳.  
  - A **Global Catalog (GC)** server (stores searchable data across the forest).  
  - A single **schema** (rules about what objects exist & their attributes).  
- Forests allow organizations to **separate environments**.  

🔑 Example:  
- Company A (Forest 1) and Company B (Forest 2) have different forests because they don’t want to share admin control.  
- If needed, they can create a **forest trust** to share resources.

---

## 🌳 Trees

- A **collection of one or more domains** that share a **continuous namespace**.  
- Domains in a tree are connected by **two-way transitive trust relationships** (meaning trust flows automatically both ways).  
- Each tree has:  
  - A root domain (e.g., `company.com`).  
  - Child domains (e.g., `hr.company.com`, `sales.company.com`).  

📌 Why Trees?  
- To reflect **organization structure** or **different geographic regions**.  
- To **delegate control** per department.  

---

## 🏰 Domains

- The **core administrative unit** of Active Directory.  
- Every object (users, computers, printers, groups) lives inside a domain.  
- Each domain has:  
  - A **unique namespace** (like `sales.company.com`).  
  - **Domain Controllers (DCs)** that store and replicate the domain database.  
  - **Security policies** (password policies, account lockout, etc.).  
  - **Authentication boundary** → logins are validated within the domain.  

📌 Why Domains?  
- They provide **isolation**, **security policies**, and **management boundaries**.  
- Useful when you need **different policies for different divisions** (e.g., IT vs. HR).  

---

## 🗂️ Organizational Units (OUs)

- Think of OUs as **folders inside a domain**.  
- OUs help organize objects for **delegation and policy application**.  
- You can:  
  - Group users, computers, or groups.  
  - Apply **Group Policy Objects (GPOs)** at the OU level.  
  - Delegate administrative rights (e.g., HR manages only `HR-Users OU`).  

📌 Why OUs?  
- To simplify management by organizing objects logically.  
- To avoid giving **domain-wide admin rights** when only OU-level rights are needed.  

---

## 🎯 Logical Structure in Action

Imagine a global company **TechWorld Inc.** 🌍

- **Forest:** TechWorld Forest  
- **Tree 1:** `techworld.com`  
  - **Domain 1:** `sales.techworld.com`  
    - **OUs:**  
      - `Sales-Users`  
      - `Sales-Computers`  
  - **Domain 2:** `hr.techworld.com`  
    - **OUs:**  
      - `HR-Users`  
      - `HR-Computers`  
- **Tree 2:** `techworld-europe.com`  
  - **Domain:** `finance.techworld-europe.com`  
    - **OUs:**  
      - `Finance-Users`  
      - `Finance-Computers`  

This way:  
- Admins in HR don’t control Sales.  
- Admins in Sales Europe can be isolated from US Sales if needed.  
- Group Policies can be different for Finance vs HR.  

---

## ✅ Key Takeaways

- **Forest** = Entire security & schema boundary 🌲.  
- **Tree** = Domains linked in a hierarchy 🌳.  
- **Domain** = Core unit with users, groups, policies 🏰.  
- **OU** = Container to organize objects & delegate rights 🗂️.  

---

📌 **In short:**  
The logical structure is **about organization, security boundaries, and delegation of control**. It defines **who manages what and how objects are grouped**.  

# 📂 Active Directory Physical Structure (Deep Dive)

The **Physical Structure** of Active Directory defines **how AD is implemented in the real world** — the servers, sites, and networks that make everything work.  

👉 While the **logical structure** is about **organization & security**, the **physical structure** is about **infrastructure & replication efficiency**.  

---

## 🖥️ Domain Controllers (DCs)

- A **Domain Controller** is a **server that runs AD DS**.  
- Stores a **copy of the Active Directory database (NTDS.dit)**.  
- Responsibilities:  
  - Authenticate users & computers (via Kerberos/NTLM).  
  - Apply policies (Group Policy processing).  
  - Replicate directory changes with other DCs.  

⚡ **Best Practices:**  
- Always deploy **at least 2 DCs per domain** (for redundancy).  
- Enable **Read-Only DCs (RODCs)** in branch offices for better security.  

---

## 🌐 Sites

- A **site** in AD represents a **physical location (like an office or data center)** that is connected by a **high-speed LAN**.  
- Sites are **not security boundaries** — they are purely for **replication and authentication efficiency**.  
- Used to control:  
  - **Replication traffic** between DCs.  
  - **Client logon behavior** (users authenticate with DCs in their own site first).  

📌 Example:  
- Site 1 = New York Office 🗽  
- Site 2 = London Office 🎡  
- Site 3 = Tokyo Office 🏯  

---

## 📡 Subnets

- Subnets represent **IP address ranges** in AD.  
- Subnets are mapped to **sites** so clients can locate the **nearest DC**.  
- Example:  
  - Subnet `10.10.1.0/24` → Mapped to **New York Site**.  
  - Subnet `10.20.1.0/24` → Mapped to **London Site**.  

🔑 Why?  
- When a client logs in, it checks its **IP address** → Maps to subnet → Finds nearest **site/DC** → Faster login!  

---

## 🔄 Replication

- Replication is how **all DCs stay updated** with the latest AD changes.  
- Two types of replication:  
  1. **Intra-site replication** (within same site) → Fast, frequent, uncompressed.  
  2. **Inter-site replication** (between sites) → Scheduled, compressed, optimized for WAN links.  

📌 Example:  
- A password change in New York must replicate to London and Tokyo DCs.  

---

## 🧩 Putting It Together

Let’s imagine **TechWorld Inc.** with three offices 🌍:  

- **Sites:**  
  - New York Site 🗽 → DC1, DC2  
  - London Site 🎡 → DC3, DC4  
  - Tokyo Site 🏯 → DC5 (RODC)  

- **Subnets:**  
  - `10.10.1.0/24` → New York  
  - `10.20.1.0/24` → London  
  - `10.30.1.0/24` → Tokyo  

- **Replication:**  
  - NY ↔ London ↔ Tokyo replication (configured based on WAN bandwidth).  

---

## ✅ Key Takeaways

- **Domain Controllers (DCs):** Servers hosting AD database & authentication.  
- **Sites:** Physical locations, optimize replication & logon traffic.  
- **Subnets:** IP ranges mapped to sites → Help clients find nearest DC.  
- **Replication:** Keeps all DCs in sync (intra-site = fast, inter-site = scheduled).  

---

📌 **In short:**  
The **physical structure = the plumbing of AD** 🚰 → how data flows between servers, sites, and networks to keep everything running smoothly.  


# 🧩 Key Services in Active Directory

Active Directory (AD) is **not just a database** — it relies on several **underlying services & protocols** to function properly.  
Without these, AD **cannot authenticate users, locate resources, or replicate data**.  

Here are the **core services that power AD**:

---

## 🌍 1. DNS Integration (Domain Name System)

### 🔹 Why DNS Matters
- **Active Directory = DNS-dependent**.  
- Every **Domain Controller (DC)** registers special records in DNS, so clients and other DCs can find them.  
- Without DNS, clients would be "lost" and unable to log in.

### 🔹 Service Records (SRV)
- When a DC comes online, it publishes **SRV records** into DNS.  
- Example:
  - `ldap._tcp.dc._msdcs.company.com` → tells clients where to find a DC.  
  - `kerberos._tcp.dc._msdcs.company.com` → tells clients where to request Kerberos tickets.  

### 🔹 Example Flow
1. Alice logs in.  
2. Her PC queries DNS for `ldap._tcp.dc._msdcs.company.com`.  
3. DNS replies with the IP of a Domain Controller.  
4. Alice’s PC connects to the DC to authenticate.  

✅ **Bottom Line:** If DNS breaks, **AD login, replication, and GPOs stop working**.  

---

## 📡 2. LDAP Protocol (Lightweight Directory Access Protocol)

### 🔹 What is LDAP?
- LDAP = a **standard directory protocol**.  
- Used to **query, search, and update** objects in the AD database.  

### 🔹 How AD Uses LDAP
- Applications use LDAP to **find users, computers, or groups**.  
- Administrators use LDAP for **scripting & automation**.  

### 🔹 Example Queries
- `ldap://dc1.company.com` → Connect to Domain Controller.  
- `(&(objectClass=user)(department=HR))` → Find all HR users.  
- `(&(objectClass=computer)(operatingSystem=Windows*))` → Find all Windows computers.  

### 🔹 Real-World Examples
- Single Sign-On (SSO) apps use LDAP to validate users.  
- HR system syncing employees → pulls user info via LDAP.  

✅ **Bottom Line:** LDAP is the **language of Active Directory**.  

---

## 🔑 3. Kerberos Authentication

### 🔹 Why Kerberos?
- Default authentication protocol in AD.  
- **Ticket-based system** → prevents sending passwords over the network.  
- Faster and more secure than NTLM.  

### 🔹 Components
1. **KDC (Key Distribution Center)** – Runs on every DC.  
   - Issues **tickets** for authentication.  
2. **TGT (Ticket-Granting Ticket)** – Proves your identity after login.  
3. **Service Ticket** – Grants access to a specific resource (like File Server).  

### 🔹 Authentication Flow
1. User logs in → sends username & encrypted info to DC.  
2. DC issues a **TGT**.  
3. When accessing a service (e.g., `\\fileserver`), the client presents the TGT to get a **service ticket**.  
4. Service verifies the ticket → grants access without asking for password again.  

### 🔹 Advantages
- Password never travels over the network.  
- Supports **SSO (Single Sign-On)**.  
- Prevents replay attacks with **timestamps**.  

✅ **Bottom Line:** Kerberos = **secure, fast, and passwordless in practice**.  

---

## 🛡️ 4. NTLM (Legacy Authentication)

*(Optional but important for interviews)*  

- Used before Kerberos became default.  
- Still exists for **backward compatibility**.  
- Less secure (relies on **challenge-response hash**).  
- Vulnerable to **pass-the-hash attacks**.  

👉 Best practice: Disable NTLM wherever possible.  

---

## 🔄 5. Replication (Behind the Scenes)

- DCs replicate changes using **multi-master replication**.  
- Uses **RPC (Remote Procedure Calls)** or **HTTP/HTTPS** depending on site links.  
- Ensures consistency:
  - A new user created in London DC → appears in New York DC after replication.  

---

# 🎯 Summary

- **DNS** = GPS 🌍 → helps clients & DCs find each other.  
- **LDAP** = Language 📡 → queries & updates AD objects.  
- **Kerberos** = Security Guard 🔑 → secure, ticket-based login.  
- **NTLM** = Old Guard 🛡️ → only for legacy use.  
- **Replication** = Messenger 🔄 → keeps all DCs in sync.  

Without these, AD = 💔.

---



