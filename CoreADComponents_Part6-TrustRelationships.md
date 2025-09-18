# Trust Relationships in Active Directory (AD)
---

## 1️⃣ What is a Trust in AD?
A **trust relationship** in AD allows **users in one domain/forest to access resources in another domain/forest** without creating duplicate accounts.  

- AD trusts are **transitive by default within a forest**, meaning trust extends automatically through the hierarchy.  
- Trusts can be **one-way** or **two-way**.  

**Example:**  
- Domain `finance.company.local` wants users in `hr.company.local` to access a shared finance folder.  
- A trust allows `hr` users to authenticate without creating separate finance accounts.

---

## 2️⃣ Types of Trusts in AD

| Type | Scope | Direction | Notes |
|------|-------|-----------|-------|
| **Parent-Child** | Within a forest | Two-way | Automatically created when a child domain is added |
| **Tree-Root** | Within a forest | Two-way | Connects a new tree to the forest root |
| **External** | Between domains in different forests | One-way or Two-way | For legacy domains or Windows NT 4.0 domains |
| **Forest Trust** | Between two forests | One-way or Two-way | Allows full access across all domains in each forest |
| **Shortcut** | Within forest | One-way or Two-way | Speeds up authentication between distant domains in the same forest |
| **Realm Trust** | Between AD and non-Windows Kerberos realms | One-way or Two-way | For integration with UNIX/Linux or MIT Kerberos |

---

## 3️⃣ Trust Direction
- **One-way trust:** Domain A trusts Domain B → Users in **B** can access **A**, but not vice versa.  
- **Two-way trust:** Both domains trust each other → Users in A and B can access resources in each other.

---

## 4️⃣ Transitivity
- **Transitive Trust:** Automatically extends trust to other domains in the hierarchy. (e.g., Parent → Child → Grandchild)  
- **Non-Transitive Trust:** Only applies to the two domains directly involved.

---

## 5️⃣ Authentication Flow
1. User from Domain B requests access to a resource in Domain A.  
2. Domain A checks the **trust path** to Domain B.  
3. Authentication request goes to **Domain B’s DC**.  
4. DC in Domain B validates credentials and issues a **ticket/token**.  
5. Domain A grants or denies access based on permissions.

---

## 6️⃣ Use Cases
- **Single Sign-On (SSO)** across multiple domains/forests  
- **Mergers & acquisitions:** Access resources in another company’s domain  
- **Cross-forest collaboration** with partners  
- **Resource sharing** without duplicating user accounts  

---

## 7️⃣ Best Practices
- Use **two-way transitive trusts** within a forest for simplicity.  
- Use **forest trusts** for cross-forest collaboration.  
- Avoid unnecessary external trusts (for security reasons).  
- **Shortcut trusts** can improve logon speed for large forests.  
- Regularly **audit trust relationships** to maintain security.

---

✅ **In short:**  
Trusts are **the highways of authentication in AD**. They let users cross domain/forest boundaries **securely and efficiently** while controlling who can access what.
