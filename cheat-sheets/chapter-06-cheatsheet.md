## PIM Quick Reference — SC-300

### Eligible vs Active
| Type | Standing Access? | Activation Needed? | Can be Permanent? |
|---|---|---|---|
| Eligible | No | Yes (MFA/justification/approval) | Yes, or time-bound |
| Active | Yes | No | Yes, or time-bound |

### Activation Requirements (per role, independently toggled)
- Azure MFA
- Justification (free text)
- Ticket/incident number
- Approval (1+ approvers) — pending request expires after 1 day if unactioned
- Max activation duration: **1–24 hours**

### Three Flavors of PIM
| Scope | Governs | Example Roles |
|---|---|---|
| PIM for Microsoft Entra roles | Directory-wide admin roles | Global Admin, User Admin, Exchange Admin |
| PIM for Azure resource roles | Azure RBAC, scoped to mgmt group/sub/RG/resource | Owner, Contributor, Reader |
| PIM for Groups | Membership/Ownership of cloud-only M365/Security groups | Member, Owner (indirect role grant via group) |

### PIM for Groups Requirements
- Group must be **cloud-only** (not synced from on-prem)
- Enable PIM per group; configure Member and Owner settings separately
- Group can then be assigned an Entra role or Azure RBAC role, granting indirect just-in-time access to all activated members

### Access Reviews for Privileged Roles
- Scope: specific Entra role or Azure resource role assignments (eligible and/or active)
- Recurrence: One-time / Weekly / Monthly / Quarterly / Annually
- Reviewer: Resource owner, selected reviewer(s), or **self-review**
- Outcome: auto-remove access if denied/no response (configurable)

### PIM Alerts (License: Entra ID P2/Governance required)
1. **Roles are being assigned outside of PIM** — direct assignment detected
2. **Roles aren't being used** — eligible role never activated
3. **Too many global administrators** — recommended standing count: **2–4**
4. **Duplicate role assignments** — same principal, multiple assignment paths

### Common Exam Traps
- Confusing "eligible" (must activate) with "active" (already granted) — questions often test which one requires MFA/approval at time of use.
- Assuming PIM for Groups works with on-prem synced groups — it does **not**.
- Forgetting PIM requires **P2/Governance**, not P1.
- Choosing direct role assignment when the scenario calls for time-bound/just-in-time access — always prefer eligible + activation over standing assignment for exam "least privilege" scenarios.
- Mixing up PIM for Entra roles (directory) vs Azure resource roles (RBAC scope) — read the scenario for "subscription/resource group" (→ Azure resource roles) vs "tenant-wide admin" (→ Entra roles).
