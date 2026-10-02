## Chapter 1 Cheat Sheet — Tenant, Users, Groups & Administrative Units

### Group Type Comparison
| Group Type | Licensing Support | Collaboration (mailbox/SharePoint/Planner) | Conditional Access Target |
|---|---|---|---|
| Security | ✅ | ❌ | ✅ |
| Microsoft 365 | ✅ | ✅ | ✅ |
| Distribution | ❌ | ❌ | ❌ |
| Mail-enabled Security | ❌ | ❌ | ✅ |

### Dynamic Membership Rule Syntax
| Element | Example | Notes |
|---|---|---|
| Equality | `user.department -eq "Finance"` | Use -eq for single-valued string attributes |
| Logical AND | `-and` | Must be dash-prefixed; lowercase `and` is invalid |
| Logical OR | `-or` | Combine multiple conditions |
| Multi-value match | `-contains` | For array attributes only (proxyAddresses, otherMails) |
| Guest filter | `user.userType -eq "Guest"` | Preferred over parsing UPN `#EXT#` |
| Max rule length | 3,072 characters | Simplify nested conditions if exceeded |

### Administrative Units (AU)
- Contain users, groups, and devices for delegated scope.
- Built-in AND custom roles can both be scoped to an AU (not exclusive to custom roles).
- Use AU scoping instead of tenant-wide role assignment for regional/departmental delegation.
- Restricted management AUs can hide member details from admins outside the AU.

### Group-Based Licensing
- Supported: Security groups, Microsoft 365 groups.
- NOT supported: Distribution groups, mail-enabled security groups.
- Conflicting service plans (e.g., Exchange Online Plan 2 vs Exchange Online Kiosk) are NEVER auto-resolved — admin must manually disable a plan or remove a duplicate direct assignment.
- Licensing errors persist until resolved; group membership sync itself is not blocked.

### Directory Roles vs Custom Roles
| Feature | Built-in Role | Custom Role |
|---|---|---|
| License required | No | Microsoft Entra ID P1/P2 |
| Permissions | Fixed, predefined | Fully customizable |
| AU scoping | ✅ | ✅ |
| Can be assigned to groups (PIM/role-assignable groups) | ✅ | ✅ |

### Users
- Member: full default directory permissions.
- Guest (B2B): restricted default permissions, controlled via External collaboration settings.
- Bulk operations: CSV-based bulk create/update/delete/invite available in the portal.

### Custom Domain Verification
- Add domain → verify via **TXT record** (preferred) or **MX record** at your DNS registrar.
- CNAME and A records are NOT used for verification.

### Owners vs Members
- Max **100 owners** per group.
- Members: effectively unlimited for practical exam purposes — owners is the tested constraint.
