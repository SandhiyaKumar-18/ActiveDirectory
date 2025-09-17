# 🏰 Domain in Active Directory

A **Domain** is one of the **key logical components** of Active Directory (AD).  
It serves as the **core security boundary** for users, computers, and resources.

---

## 🔹 What is a Domain?

- A **Domain** is a collection of **objects** (users, groups, computers, printers, etc.) that **share a common AD database**.  
- Each domain has:  
  - Its own **Security Accounts Manager (SAM) database / AD database)**  
  - Its own **Group Policy Objects (GPOs)**  
  - Its own **administrative scope**  

✅ Think of a Domain as a **fenced garden** 🌳:  
- Everything inside is controlled by a set of rules (permissions, policies).  
- Access is limited unless explicitly granted.

---

## 🔹 Why is a Domain a Core Security Boundary?

1. **Authentication Boundary**  
   - Users in one domain **cannot authenticate** in another domain unless a **trust** exists.  

2. **Authorization Boundary**  
   - Permissions and access control are **enforced per domain**.  
   - Groups and ACLs (Access Control Lists) are **domain-specific**.  

3. **Policy Enforcement**  
   - GPOs are applied **per domain**.  
   - Security policies (password rules, account lockout) are **domain-specific**.  

4. **Administrative Delegation**  
   - Admins are granted rights **within a domain**.  
   - Admins from one domain **cannot directly control objects in another domain** without trust.  

---

## 🔹 Domain Components

- **Domain Controllers (DCs)** → Servers that host the AD database for the domain.  
- **Users & Groups** → Managed centrally within the domain.  
- **Organizational Units (OUs)** → Subdivide domain objects for delegation and policy.  
- **Group Policies** → Applied at domain, OU, or site level.

---

## 🔹 Domain Trusts

- Domains can **trust each other** to allow cross-domain authentication:  
  - **One-way trust** → Domain A trusts Domain B.  
  - **Two-way trust** → Domain A ↔ Domain B trusts each other.  
- Trusts maintain the **security boundary** while allowing collaboration.  

---

## 🎯 Simple Analogy

- Domain = **castle 🏰**  
  - Walls = security boundary  
  - Guards = Domain Controllers (DCs)  
  - Inside = users, groups, computers  
  - Gate = trust relationships (allowing certain outsiders in)  

---

## ✅ Key Takeaways

- A **domain is the core security boundary** in AD.  
- Controls **authentication, authorization, policy enforcement, and administration**.  
- Multiple domains can exist in a forest, connected via **trusts**.  
- Always think **“What can cross this boundary?”** → that’s the essence of domain security.  

---

# 🏰 Active Directory Domain: Core Security Boundary

A **Domain** in Active Directory (AD) is one of the most important logical structures.  
It acts as the **core security boundary**, defining authentication, authorization, and administrative scope.  

Think of a **Domain as a castle 🏰**:
- Walls = security boundary  
- Guards = Domain Controllers (DCs)  
- Inside = users, groups, computers, printers  
- Gates = trust relationships for outsiders  

---

## 🌐 1. What is a Domain?

- A **Domain** is a **collection of objects** (users, groups, computers, printers, policies) that share a **common AD database**.  
- Each domain has:  
  - Its **own database** (NTDS.dit)  
  - Its **own Group Policies (GPOs)**  
  - Its **own administrative scope**  

✅ Domains define **who belongs where** and **who can do what**.  

---

## 🔹 2. Domain Names

- **FQDN (Fully Qualified Domain Name)** → e.g., `company.com`  
- **NetBIOS Name (Legacy)** → e.g., `COMPANY`  
- Both names exist for compatibility:  
  - FQDN → modern DNS-based systems  
  - NetBIOS → older Windows systems & legacy applications  

---

## 🖥️ 3. Domain Controllers (DCs)

- Every domain has **one or more DCs**.  
- DCs store a **replicated copy of the domain database**.  
- Responsibilities:  
  1. **Authentication** – verify user/computer credentials  
  2. **Authorization** – decide access rights to resources  
  3. **Replication** – synchronize domain objects across DCs  
  4. **Policy enforcement** – apply domain GPOs  

---

## 🌍 4. Global Catalog (GC)

- A **special DC** that stores a **partial replica of all objects in the forest**.  
- Key functions:  
  - Enables **cross-domain object searches**  
  - Supports **forest-wide logins**  
  - Evaluates **universal group membership**  
- Typically, **at least one GC per site** is recommended.  

---

## ⚡ 5. Domain Functional Levels

Domains have **functional levels** which determine the **available AD features**:  

| Functional Level | Supported OS | Key Feature Example |
|-----------------|--------------|------------------|
| Windows Server 2012 R2 | 2012 R2+ | Dynamic Access Control |
| Windows Server 2016 | 2016+ | Privileged Access Management |
| Windows Server 2022 | 2022+ | Enhanced security & latest AD features |

- **Raising a domain functional level** requires all DCs to run the **required OS version**.  

---

## 🔑 6. Security Boundary

Domains act as the **core security boundary**:  
1. **Authentication Boundary** – Users cannot log in across domains unless **trust exists**.  
2. **Authorization Boundary** – Access to resources is limited to the domain unless cross-domain permissions are configured.  
3. **Policy Enforcement** – GPOs applied at domain level enforce security rules.  
4. **Administrative Delegation** – Admins are scoped per domain; cross-domain access needs trust.  

---

## 🔄 7. Trust Relationships

- Trusts allow controlled **cross-domain access**:  
  - **One-way trust** → Domain A trusts Domain B  
  - **Two-way trust** → Domain A ↔ Domain B trust each other  
- Trusts **maintain security boundaries** while allowing collaboration.  

---

## 📂 8. Organizational Units (OUs)

- Domains are subdivided into **Organizational Units**:  
  - Logical containers for users, groups, computers, and resources.  
  - Allow **delegation of administrative control** without giving full domain rights.  
  - Example: `OU=HR,DC=company,DC=com`  

---

## 📜 9. Default Domain Policy & GPOs

- Each domain has a **Default Domain Policy** automatically applied to all users/computers.  
- Contains security settings like:  
  - Password policies  
  - Account lockout policies  
  - Kerberos ticket lifetimes  

---

## 🏢 10. Sites & Domain Controllers

- Domains can span **multiple physical locations**.  
- **Sites** represent physical network topology.  
- DCs in the same site are used for **local authentication** and **optimized replication**.  
- Helps reduce **WAN traffic** and improves **login performance**.  

---

## 🔹 11. Domain Objects

Objects inside a domain include:  

| Object Type | Description |
|-------------|-------------|
| User 👩‍💻 | Employee accounts |
| Group 👥 | Collection of users or computers |
| Computer 💻 | Domain-joined computers |
| Printer 🖨️ | Network printers |
| Policy 📜 | GPOs applied to users/computers |

---

## 🔹 12. Analogy for Memory

- **Domain = Castle 🏰**  
- Walls → Security boundary  
- Guards → Domain Controllers (DCs)  
- Rooms → Organizational Units (OUs)  
- People inside → Users & Groups  
- Rules → Group Policies  
- Gates → Trust relationships  

---

## 🔹 13. Summary of Domain

- Domains are **logical and security boundaries** in AD.  
- Control **authentication, authorization, policy enforcement, and administration**.  
- Contain **DCs, OUs, users, groups, and GPOs**.  
- Can have **trusts** to collaborate across domains.  
- Functional levels define **available AD features**.  
- Sites optimize **replication and authentication** across physical networks.  

---

### 🎯 Key Takeaways

1. **Core Security Boundary** of AD  
2. **DCs replicate objects and enforce policies**  
3. **Global Catalog enables forest-wide searches**  
4. **Functional levels unlock AD features**  
5. **Trusts allow secure collaboration across domains**  
6. **OUs allow delegation and organization**  
7. **Default Domain Policy enforces basic security rules**  

---

## 🖼️ Visual Representation (ASCII)


