## Chapter 10 Cheat Sheet: Lifecycle Workflows & Application Access Governance

### Lifecycle Workflow Templates
| Category | Template | Trigger |
|---|---|---|
| Joiner | Onboard new hire employee | employeeHireDate |
| Joiner | Onboard new hire employee (with pre-hire tasks) | employeeHireDate (offset before start) |
| Mover | Onboard employee transferring between departments | Attribute change (e.g., department) |
| Leaver | Offboard an employee | employeeLeaveDateTime (scheduled) |
| Leaver | Real-time employee termination | employeeLeaveDateTime (immediate) |
| Leaver | Post-offboarding of an employee | employeeLeaveDateTime + offset after |

### Execution Condition = Trigger + Scope
- **Trigger**: hire date, leave date, attribute change, on-demand, or scheduled
- **Scope**: rule-based filter on user attributes (e.g., `department eq 'Sales'`)
- Workflow fires only when BOTH match

### Key Limits
| Item | Limit |
|---|---|
| Workflows per tenant | 50 |
| Tasks per workflow | 25 |
| On-demand run batch | 100 users |
| Default schedule interval | Every 3 hours |

### Custom Task Extensions
- Extend beyond built-in tasks by calling an **Azure Logic App**
- Requires an app registration with custom task extension permission
- Use for: external HR API calls, ticketing systems, custom notifications

### User Consent Settings
| Setting | Risk | Use Case |
|---|---|---|
| Do not allow user consent | Lowest risk, highest admin overhead | High-security tenants |
| Allow consent for verified publishers, selected permissions | Balanced (recommended) | Most orgs |
| Allow user consent for all apps | Highest risk | Not recommended |

### Admin Consent Workflow
- Enabled when user consent is blocked/limited and app needs approval
- Reviewers: Global Admin, Cloud App Admin, Application Admin, or designated reviewers
- Request expiration: **default 30 days**, configurable 1–90 days
- Reviewer gets email notification; can approve/deny with optional justification

### App Governance (Microsoft Defender for Cloud Apps)
- Detects: risky/overprivileged OAuth apps, unused permissions, anomalous app behavior
- Provides policies to alert or auto-remediate risky app permissions
- Requires Defender for Cloud Apps (separate from Entra ID P2)

### Access Reviews for App Permissions
- Identity Governance access reviews can target **application/service principal access**, not just group/role membership
- Reviewers: app owners, designated approvers
- Used to periodically certify that granted delegated/application permissions are still required

### Exam Gotchas
1. Real-time termination ≠ standard leaver — real-time bypasses the 3-hour schedule
2. Mover trigger is an **attribute change**, not a date-based trigger
3. Admin consent workflow only appears when user consent is set to **limited/blocked** for that permission tier
4. App governance requires Defender for Cloud Apps — it is NOT a native Entra ID P1/P2 feature
5. Custom task extensions require Logic Apps + correct API permission — a common wrong answer is choosing Power Automate
