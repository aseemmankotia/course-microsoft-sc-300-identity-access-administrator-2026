## Chapter 8: Managed Identities & Workload Identity Federation — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | What happens to a system-assigned managed identity when its host resource is deleted? | It's automatically deleted along with the resource. Exam tip: strict 1:1 lifecycle binding — no orphaned identities. |
| 2 | Max number of federated credentials allowed on a single Azure AD application? | 20. Exam tip: scenarios federating many repos/clusters to one app must respect this limit. |
| 3 | System-assigned vs user-assigned: which can be pre-created before the target resource exists? | User-assigned. It's a standalone Azure resource with an independent lifecycle, assignable to zero, one, or many resources. |
| 4 | GitHub Actions federated credential subject format for a push to branch 'main'? | repo:<org>/<repo>:ref:refs/heads/main. Exam tip: subject must exactly match the trigger context. |
| 5 | Default audience value for an Azure AD federated credential? | api://AzureADTokenExchange — the standard audience Azure AD expects when validating the external OIDC token. |
| 6 | Can a system-assigned managed identity be shared across multiple Azure resources? | No. Exam tip: system-assigned is strictly 1:1; use user-assigned to share across resources. |
| 7 | What credential burden does workload identity federation remove vs a stored client secret? | No secret value is stored or transmitted — a short-lived external OIDC token is exchanged for an Azure AD token. Exam tip: eliminates rotation and leakage risk. |
| 8 | Which requires manual credential rotation: managed identity or service principal with client secret? | Service principal with client secret. Managed identity credentials are rotated automatically by Azure AD, invisible to the admin. |
| 9 | Least-privilege RBAC rule for non-human identities? | Scope role assignment to the narrowest resource (not subscription/RG) and grant only the minimum built-in or custom data-plane role needed. Exam tip: exam favors container/resource-scoped Reader-type roles over Contributor/Owner. |
| 10 | AKS workload identity federation: what must the Kubernetes service account be annotated with? | azure.workload.identity/client-id — the client ID of the managed identity/app registration. Pairs with the AKS OIDC issuer URL as the federated credential issuer. |
| 11 | Can a managed identity be used across Azure AD tenants? | No. Managed identities (system- or user-assigned) never work cross-tenant, even though a user-assigned identity can span subscriptions in the same tenant. |
| 12 | GitHub Actions federated credential subject for a GitHub Environment named 'production'? | repo:<org>/<repo>:environment:production. Exam tip: use this format when deployment gating relies on a GitHub Environment approval. |
