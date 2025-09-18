
## 🏗️ FSMO Roles
Active Directory has **5 Flexible Single Master Operation (FSMO) roles**:

### FSMO stands for Flexible Single Master Operations.

In Active Directory (AD), most changes (like creating users, updating group memberships) can happen on any domain controller because AD is multi-master. But some specific tasks must be handled by a single designated domain controller to avoid conflicts. These tasks are called FSMO roles.

| Role | Scope | Purpose |
|------|-------|---------|
| **Schema Master** | Forest | Controls updates/changes to the AD schema |
| **Domain Naming Master** | Forest | Manages addition/removal of domains in the forest |
| **RID Master** | Domain | Allocates RID pools to domain controllers for unique SIDs |
| **PDC Emulator** | Domain | Handles time sync, password changes, legacy support |
| **Infrastructure Master** | Domain | Updates references from objects in other domains |

## 🔄 Replication
- **Intra-site replication:** Between DCs in the same site (fast, frequent, default 15 min)
- **Inter-site replication:** Between DCs in different sites (optimized for WAN, scheduled)
- **AD replication topology:** Managed by Knowledge Consistency Checker (KCC), ensures DCs replicate efficiently

## 📂 Schema
- **Extending AD schema:** Add attributes/classes for new applications
- Use `adprep /forestprep` and `adprep /domainprep` when extending schema
- Always test in lab before production

## 🌍 Sites & Subnets
- Sites represent **physical locations**
- Subnets assigned to sites improve **authentication efficiency** and replication
- AD uses **site-aware DC selection** for logon and service requests

## 🧭 DNS in AD
- **Forward lookups:** Name → IP resolution
- **Reverse lookups:** IP → Name resolution
- **SRV records:** Locate AD services (e.g., `_ldap._tcp.dc._msdcs.<domain>`)

## ⏳ Timeline
- **Week 8**: Focus on FSMO, replication, schema, sites & subnets, DNS

---

## 🛠️ Lab Ideas
1. **FSMO Role Transfer**
   - Use GUI (`ntdsutil` or Active Directory Users and Computers)  
   - Test both **seizing** and **transferring** roles

2. **Simulate Inter-Site Replication**
   - Create multiple sites in AD Sites and Services
   - Assign subnets and simulate WAN replication
   - Observe replication latency using `repadmin /showrepl`

