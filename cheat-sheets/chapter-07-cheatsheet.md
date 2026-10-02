## Chapter 7 Cheat Sheet — App Registrations, Service Principals & API Permissions

### Object Model
| Object | Scope | Created When | Purpose |
|---|---|---|---|
| Application object | Home tenant only (1 per app) | App registration created | Global template/definition |
| Service principal | Every tenant that uses the app | App registered (home tenant) OR consented (other tenants) | Local security principal used for auth/authz — shown as **Enterprise Application** in portal |

**Rule:** Enterprise Application = Service Principal. Registering an app auto-creates a home-tenant SP; each external tenant that consents gets its own SP copy.

### Sign-in Audience Options
| Value | Meaning |
|---|---|
| AzureADMyOrg | Single tenant |
| AzureADMultipleOrgs | Multi-tenant (any Azure AD org) |
| AzureADandPersonalMicrosoftAccount | Multi-tenant + personal MSA |
| PersonalMicrosoftAccount | Personal MSA only |

### Delegated vs Application Permissions
| | Delegated | Application |
|---|---|---|
| Acting as | Signed-in user | The app itself |
| Needs user present? | Yes | No |
| Effective access | Capped by user's own privileges | Full permission scope |
| Consent | User consent (if allowed) OR admin consent | **Admin consent always required** |

### Consent Settings (Tenant-wide, User Consent)
1. Do not allow
2. Allow for verified publishers / low-risk permissions (recommended balance)
3. Allow for all apps

### Admin Consent Workflow
- Must be **enabled** + at least 1 **reviewer** assigned (Global Admin, Cloud App Admin, Application Admin, or designated user/group)
- Request expiration: default **30 days**, configurable 1–365
- Blocked users can submit a request instead of being denied outright

### Credentials
| Type | Max Lifetime | Recommendation |
|---|---|---|
| Client secret | 24 months | Rotate frequently; easier to leak |
| Certificate | No forced max (admin-set) | Preferred for production/higher security |

### App Roles
- Defined in app **manifest** (`appRoles`) on the app registration
- **Assigned** to users/groups/other SPs on the **Enterprise Application**
- Surfaces in token as **`roles`** claim
- Used for custom in-app authorization (not the same as delegated/application API permissions)

### Service Principal Types
- **Application** — tied to an app registration
- **Managed Identity** — auto-managed, for Azure resources
- **Legacy** — pre-dates the app registration model

### Common Traps
- Assuming app registration and enterprise app are the *same* object (they are linked but distinct: application object vs service principal).
- Choosing delegated permissions for unattended/daemon scenarios (no signed-in user → must be application permission).
- Forgetting application permissions **always** need admin consent — never user consent.
- Picking client secret over certificate when the scenario asks for the 'most secure' credential option.
