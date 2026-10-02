## Chapter 8 Cheat Sheet — Managed Identities & Workload Identity Federation

### Exam Domain
Plan and implement workload identities (20-25%)

### System-Assigned vs User-Assigned
| Feature | System-Assigned | User-Assigned |
|---|---|---|
| Lifecycle | Tied 1:1 to resource; auto-deleted with it | Independent Azure resource; persists until manually deleted |
| Sharing | Cannot be shared | Can be assigned to many resources |
| Pre-provisioning | No — created with resource | Yes — create before attaching |
| Use case | Single-resource, disposable workloads | Shared identity across multiple resources/environments |

### Workload Identity Federation vs Stored Secrets
| Aspect | Federation | Stored Secret/Cert |
|---|---|---|
| Credential storage | None — external OIDC token exchanged for Azure AD token | Secret/cert stored in external system |
| Rotation | Not needed | Manual, periodic |
| Leak risk | Eliminated (no long-lived secret) | Present |
| Typical use | GitHub Actions, AKS, other OIDC-compatible external workloads | Legacy service principal auth |

### Federated Credential Config Essentials
- Configured on an **App Registration** (federated credentials blade)
- Requires: Issuer URL, Subject identifier, Audience (default `api://AzureADTokenExchange`)
- **Max 20 federated credentials per application**

### GitHub Actions Subject Formats
| Trigger | Subject |
|---|---|
| Push to branch | `repo:org/repo:ref:refs/heads/<branch>` |
| Tag push | `repo:org/repo:ref:refs/tags/<tag>` |
| Pull request | `repo:org/repo:pull_request` |
| Environment deploy | `repo:org/repo:environment:<name>` |

### AKS Workload Identity Federation
1. Enable OIDC issuer on AKS cluster
2. Create federated credential on app/managed identity: issuer = AKS OIDC URL, subject = `system:serviceaccount:<namespace>:<sa-name>`
3. Annotate Kubernetes service account: `azure.workload.identity/client-id: <clientId>`
4. Label pod spec: `azure.workload.identity/use: "true"`

### Least-Privilege RBAC for Non-Human Identities
- Scope assignments to the **narrowest resource** (container, single resource) — never subscription-wide by default
- Prefer **data-plane specific roles** (e.g., Storage Blob Data Reader) over Contributor/Owner
- Use **custom roles** when built-in roles grant excess actions
- Review and remove unused role assignments regularly (governance)

### Common Exam Traps
- Assuming system-assigned identities can be reused across a replacement resource — they cannot
- Assigning a managed identity directly to a GitHub-hosted runner or Kubernetes pod — not supported; federation is required
- Choosing Contributor/Owner for "least privilege" scenarios instead of a scoped data role
- Confusing `environment:` subject (GitHub Environments) with `ref:refs/heads/` (branch push)

### Governance Tip
Audit federated credential subjects and app registration owners periodically; unlike managed identities, app registrations used for federation still require manual lifecycle governance.
