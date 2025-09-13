# ⚙️ Active Directory Domain Services (AD DS) Installation Guide – Windows Server 2025

> Step-by-step guide to install AD DS using **Server Manager** on Windows Server 2025.

---

## 🖥️ Prerequisites

Before you begin:

1. **Windows Server 2025** installed.  
2. **Static IP address** assigned.  
3. **Administrator account** with a strong password.  
4. Proper **computer name** configured.  
5. Sufficient **disk space & memory**.  
6. Optional: Internet connectivity for updates.  

> Note: Windows Server 2025 includes **modernized UI, Bluetooth support, and enhanced AD security features**.  

---

## 🚀 Step 1: Open Server Manager

- Click **Start** → Type `Server Manager` → Press **Enter**.  
- Server Manager dashboard opens.  

---

## 🚀 Step 2: Add Roles and Features

1. Click **Manage → Add Roles and Features**.  
2. On **Before You Begin** page → Click **Next**.  

---

## 🚀 Step 3: Installation Type

- Select **Role-based or feature-based installation** → Click **Next**.  

---

## 🚀 Step 4: Server Selection

- Choose **Select a server from the server pool** → Highlight your server → Click **Next**.  

---

## 🚀 Step 5: Select Server Roles

1. Check **Active Directory Domain Services**.  
2. Popup: “Add features required for Active Directory Domain Services?” → Click **Add Features**.  
3. Click **Next**.  

---

## 🚀 Step 6: Select Features

- No extra features needed → Click **Next**.  

---

## 🚀 Step 7: AD DS Information

- Review AD DS information → Click **Next**.  

---

## 🚀 Step 8: Confirm Installation Selections

- Optionally, check **Restart the destination server automatically if required**.  
- Click **Install**.  

> Wait for installation to complete.  

---

## 🚀 Step 9: Promote Server to Domain Controller

- Click **Promote this server to a domain controller** (yellow notification in Server Manager).  

---

## 🚀 Step 10: Deployment Configuration

- Choose one of the following:
  - **Add a new forest** → For first domain.  
  - **Add a domain controller to an existing domain** → Existing domain.  
  - **Add a new domain to an existing forest** → Child domain.  
- Enter **Root domain name** (e.g., `corp.local`) → Click **Next**.  

---

## 🚀 Step 11: Domain Controller Options

- Select **Forest functional level** → Default: Windows Server 2025.  
- Select **Domain functional level** → Default: Windows Server 2025.  
- DNS server: check (usually selected by default).  
- Enter **DSRM password** → Click **Next**.  

---

## 🚀 Step 12: DNS Options

- Ignore delegation warnings → Click **Next**.  

---

## 🚀 Step 13: Additional Options

- NetBIOS domain name auto-populated → Click **Next**.  

---

## 🚀 Step 14: Paths

- Database folder → Default: `C:\Windows\NTDS`  
- Log files folder → Default: `C:\Windows\NTDS`  
- SYSVOL folder → Default: `C:\Windows\SYSVOL`  
- Click **Next**.  

---

## 🚀 Step 15: Review Options

- Review configuration → Click **Next**.  

---

## 🚀 Step 16: Prerequisites Check

- Wizard checks prerequisites → Ensure all pass → Click **Install**.  

---

## 🚀 Step 17: Installation & Reboot

- AD DS is installed → Server automatically **reboots**.  

---

## 🚀 Step 18: Verification

1. Log in using **domain credentials**.  
2. Open **Server Manager → Tools → Active Directory Users and Computers (ADUC)**.  
3. Confirm domain exists → Create a test user.  

---

## ✅ Quick Recap Table

| Step | Action |
|------|--------|
| 1 | Open Server Manager |
| 2 | Add Roles and Features |
| 3 | Select Role-based Installation |
| 4 | Select Server |
| 5 | Select AD DS Role → Add Features |
| 6 | Features → Next |
| 7 | AD DS Info → Next |
| 8 | Confirm & Install |
| 9 | Promote server to Domain Controller |
| 10 | Deployment Configuration (New Forest / Domain) |
| 11 | Domain Controller Options (Functional Level, DNS, DSRM) |
| 12 | DNS Options → Next |
| 13 | Additional Options (NetBIOS) → Next |
| 14 | Paths → Next |
| 15 | Review Options → Next |
| 16 | Prerequisites Check → Install |
| 17 | Installation completes → Server reboots |
| 18 | Verify via ADUC & create test users |

---

💡 **Pro Tips for Windows Server 2025**

- Take advantage of **enhanced AD security features**: confidential attributes, default machine account passwords, and AD object repair.  
- Use **Bluetooth keyboards/mice** if needed — 2025 now supports it.  
- Consider **hybrid Azure integration** if you plan cloud connectivity.  
- Always have **at least 2 Domain Controllers** for redundancy.  

---

