# 📡 LDAP (Lightweight Directory Access Protocol) in Active Directory

LDAP is the **language that clients and applications use to talk to Active Directory**.  
Without LDAP, AD would just be a database with no way to **query, search, or modify objects**.

---

## 🔹 What is LDAP?

- Stands for **Lightweight Directory Access Protocol**.  
- Standard protocol for **accessing directory services**.  
- Works over **TCP/IP** (ports 389 for plain, 636 for SSL/LDAPS).  
- Can be used by:  
  - Windows clients  
  - Linux/Unix clients  
  - Applications like Exchange, SharePoint, HR systems  

✅ Think of LDAP as a **translator** between your app and AD.

---

## 🔹 LDAP in Active Directory

LDAP is used to:

1. **Search for objects**  
   - Users, groups, computers, printers, etc.  
   - Example query:  
     ```
     (&(objectClass=user)(department=HR))
     ```
     → Finds all HR users.

2. **Read object attributes**  
   - Name, email, group membership, phone, etc.  

3. **Modify objects**  
   - Add users, change passwords, update attributes.  

4. **Authentication** (in combination with Kerberos or NTLM)  
   - Applications can bind to LDAP to validate credentials.

---

## 🔹 LDAP Bind Types

1. **Anonymous Bind**  
   - No credentials required.  
   - Usually **disabled in AD** for security.  

2. **Simple Bind**  
   - Username + password sent to the server.  
   - Not secure unless using **SSL/TLS**.  

3. **SASL Bind** (Simple Authentication and Security Layer)  
   - Supports Kerberos or other secure authentication.  
   - Default in AD environments.  

---

## 🔹 LDAP Structure

LDAP queries AD using a **hierarchical path**:  

