## Chapter 9 Cheat Sheet: Entitlement Management & Access Reviews

### Hierarchy
Catalog (container) → Access Package (bundle of resources) → Policy (requestor scope + approval + lifecycle)

### Supported Resource Types in a Catalog
| Resource | Supported? |
|---|---|
| Cloud Azure AD security group | Yes |
| Microsoft 365 group / Team | Yes |
| SharePoint Online site | Yes |
| Azure AD enterprise application | Yes |
| On-prem synced security group | No |

### Requestor Scope Options
| Scope | Use Case |
|---|---|
| Specific users and groups | Named individuals/teams |
| All members of your directory | Any internal employee |
| All users incl. connected orgs | Broad internal + known partners |
| Users not in your directory (connected org) | Partner users pre-B2B invite |

### Approval Policy
- Max **2** approval stages
- Each stage: choose approvers (specific, manager, sponsor) + fallback/escalation approver + response time limit
- Requestor justification can be required

### Connected Organizations
| Type | Notes |
|---|---|
| Azure AD (Entra) | Another Microsoft Entra tenant |
| Other directory | Non-Azure AD identity source (e.g., Google) |
- Enables requestor scope targeting before a formal B2B invite is created; invite auto-generated on request approval.

### Access Reviews
| Setting | Options |
|---|---|
| Reviewer | Self-review, Manager, Group owners, Specific reviewer(s) |
| Recurrence | One-time, Weekly, Monthly, Quarterly, Semi-Annually, Annually |
| Duration | Must be ≤ recurrence interval |
| Auto-apply results | On/Off — removes need for manual 'Apply results' |
| If reviewers don't respond | No change / Approve / Deny (Remove) / Take recommendation |

**Gotcha:** Without auto-apply enabled, non-response NEVER auto-removes access — admin must click Apply Results manually.

### Terms of Use
- Document must be **PDF**
- Optional expiration: specific date or every N days → forces re-acceptance
- Can require per-device acceptance
- Can be a Conditional Access grant control

### Assignment Lifecycle
- Duration: No expiration / Specific date / N days-hours
- Expiration notifications sent before removal
- Requestors can request extension prior to expiry if policy allows

### Exam Focus
- Heavily tested: resource types eligible for packages, 2-stage approval limit, connected-org requestor scope, auto-apply + non-response fallback combo
- Distinguish: group-owner review (membership-focused) vs self-review (individual attestation)
