# Chapter 8 Lab: Managed Identities & Workload Identity Federation

**Estimated time:** 20 minutes

## Exercise

Enable a system-assigned managed identity on an Azure VM, grant it a least-privilege RBAC role on a storage account, then configure a federated credential for a GitHub Actions workflow to authenticate without a stored secret

## Key takeaway

Managed identities and workload identity federation both remove the need to manage secrets, but only for identities scoped to Azure or federated OIDC providers.
