# 🌳 Active Directory Tree

A **Tree** in Active Directory is a **hierarchical arrangement of one or more domains** that share a **contiguous namespace** and are linked by **automatic trust relationships**.  
Think of it as a **family tree 👨‍👩‍👧‍👦** of domains inside a forest 🌲.

---

## 🔹 What Makes a Tree?

1. **Contiguous Namespace 🌐**
   - All domains in a tree share the same root DNS name.
   - Example:
     - Root Domain → `company.com`
     - Child Domain → `sales.company.com`
     - Another Child → `hr.company.com`

   ✅ They all extend from the same root namespace → `company.com`.

---

2. **Hierarchical Relationships 🏗️**
   - The **Root Domain** is the first domain created in the tree.
   - Additional domains become **child domains**.
   - Child domains can have their own **sub-child domains**, creating a hierarchy.

---

3. **Trust Relationships 🤝**
   - Trust between domains in a tree is:
     - **Two-way** → both domains trust each other.
     - **Transitive** → if A trusts B, and B trusts C → A trusts C automatically.
   - This makes resources **shareable across domains** in the tree.

---

4. **Shared Schema & Global Catalog 📚**
   - All domains in the tree share:
     - The same **AD schema** (blueprint of all object types).
     - The same **global catalog** for searching across the tree.

---

5. **Security Boundary 🚧**
   - ❌ The tree itself is **not a security boundary**.
   - ✔️ The **domain** is the true security boundary.
   - Trees exist for **hierarchy & namespace consistency**, not isolation.

---

## 🌍 Visual Example of a Tree
``` yaml

            🌳 Tree: company.com
               🏰 Root Domain: company.com
                    ├── 🏰 Child Domain: sales.company.com
                    │        └── 🏰 Sub-Child Domain: eu.sales.company.com
                    └── 🏰 Child Domain: hr.company.com
```


- Root = `company.com`
- Child = `sales.company.com`, `hr.company.com`
- Sub-child = `eu.sales.company.com`

---

## 🎯 Analogy

- **Tree in a forest 🌳**:
  - **Trunk** = Root Domain (`company.com`)
  - **Branches** = Child Domains (`sales.company.com`, `hr.company.com`)
  - **Twigs** = Sub-Child Domains (`eu.sales.company.com`)
- All are part of **the same tree** because they grow from the same trunk.

---

## ✅ Key Takeaways

- A **Tree** = one or more domains that share:
  - A **contiguous DNS namespace**  
  - **Two-way, transitive trust**  
  - **Common schema & global catalog**  
- **Root domain** = the first domain created in the tree.  
- **Domain = security boundary**, **Tree = logical hierarchy**.  

---
