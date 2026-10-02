## Chapter 2 Cheat Sheet — External Identities & Hybrid Identity Sync

### Authentication Method Decision Matrix
| Method | Password Leaves On-Prem? | Requires On-Prem Servers Beyond Connect? | AD Down = Sign-in Fails? |
|---|---|---|---|
| PHS | Hash of hash synced to cloud | No | No (cloud validates) |
| PTA | Never — real-time validation | Yes, 1+ (recommend 3) lightweight agents | Yes |
| Federation (AD FS) | Never | Yes, AD FS + WAP farm | Yes (single point of failure) |

**Exam rule of thumb:** "No password data ever leaves datacenter, no new infra" → PTA. "Need SSO but simplest, cloud-only" → PHS. "Already have complex claims/smart card/on-prem MFA" → Federation.

### Seamless SSO
- Works with PHS and PTA only, NOT federation.
- Creates `AZUREADSSOACC` computer object in on-prem AD.
- Uses Kerberos with an AES256 key for silent ticket-based sign-in.

### Sync Intervals
| Sync Type | Default Interval |
|---|---|
| Delta sync (general attributes) | 30 minutes |
| Password Hash Sync | 2 minutes |

### Staging Mode
- Second Connect server, identical config.
- Imports/syncs but does **not export** to AD or Entra ID.
- Used for safe hardware migration, config testing, DR failover.
- Promote by disabling staging mode on new server.

### Entra Connect vs Cloud Sync
| Feature | Entra Connect (full) | Cloud Sync |
|---|---|---|
| Agent weight | Heavy sync engine | Lightweight provisioning agents |
| Multi-forest complexity | Handles complex topologies | Best for simple multi-forest |
| Auth methods supported | PHS, PTA, Federation | PHS only |
| Custom sync rules | Full support | Limited |

### B2B Collaboration vs B2B Direct Connect
| Feature | B2B Collaboration | B2B Direct Connect |
|---|---|---|
| Guest object created locally? | Yes | No |
| Use case | General guest access to apps/resources | Teams shared channels |
| Trust config | Guest invitation + redemption | Cross-tenant access mutual trust (must enable explicitly) |
| Default enabled? | Yes | No — blocked by default |

### Cross-Tenant Access Settings
- **Inbound trust settings**: trust another tenant's MFA / compliant device / hybrid-joined device claims (avoids duplicate MFA).
- **Outbound settings**: control what your users can access in other tenants.
- Default B2B collaboration trust = Allow all; B2B direct connect = Block until configured.

### External Collaboration Settings
- **Guest invite restrictions**: Everyone (default) → Members + specific roles → Only specific admin roles → No one.
- **Guest access restrictions**: Same as members (default, broad directory read) → Limited access → Most restrictive.

### Common Exam Traps
1. Assuming PHS = passwords stored in cloud (it's a hash of a hash, one-way, non-reversible).
2. Confusing B2B collaboration (creates guest object) with B2B direct connect (no local object, Teams-only).
3. Forgetting federation still needs PHS enabled as DR backup — tested explicitly as a best practice.
