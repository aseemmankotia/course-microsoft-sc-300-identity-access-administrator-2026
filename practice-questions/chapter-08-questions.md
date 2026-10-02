## Chapter 8: Managed Identities & Workload Identity Federation — Practice Questions

**Q1.** A company runs an Azure VM that needs to access Key Vault. The VM will be replaced with a new VM next month, and the identity's role assignments should be reusable on the replacement VM without reconfiguring RBAC. Which identity type should be used?

A) System-assigned managed identity
B) Service principal with client secret
C) User-assigned managed identity
D) Service principal with certificate

<details>
<summary>Answer</summary>

**Correct: C**

User-assigned managed identities are standalone resources with an independent lifecycle, so their RBAC assignments persist and can be reattached to a new VM.

**Why the others are wrong:**
- System-assigned identity is deleted automatically when the VM is deleted; it cannot be reused on a new resource.
- A client secret requires manual storage and rotation, defeating the purpose of a managed credential.
- A certificate-based service principal still requires manual certificate lifecycle management.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A GitHub Actions workflow needs to deploy to Azure without storing any Azure credentials as GitHub secrets. Which configuration should you implement?

A) Store a service principal client secret as an encrypted GitHub secret
B) Configure a self-hosted runner with a managed identity assigned to it
C) Use a system-assigned managed identity assigned to the GitHub Actions runner
D) Configure a federated credential on an app registration scoped to the GitHub repo and branch

<details>
<summary>Answer</summary>

**Correct: D**

Workload identity federation lets Azure AD trust a GitHub OIDC token for a specific repo/branch subject, issuing an Azure AD token with no stored secret.

**Why the others are wrong:**
- Storing a secret in GitHub is exactly what federation is designed to avoid.
- GitHub-hosted runners are not Azure resources and cannot have a managed identity assigned; this doesn't establish trust with GitHub's OIDC token.
- Managed identities can only be assigned to Azure resources, not GitHub Actions runners.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** An AKS pod needs to call Microsoft Graph without storing any secrets in the cluster. Which single combination correctly enables this?

A) An app registration federated credential referencing the AKS OIDC issuer URL AND a Kubernetes service account annotated with the client ID
B) System-assigned managed identity on the AKS cluster AND a Key Vault secret
C) A user-assigned managed identity attached directly to each pod AND a stored client secret rotated every 90 days
D) A service principal with certificate authentication AND the Key Vault CSI driver

<details>
<summary>Answer</summary>

**Correct: A**

AKS workload identity federation pairs the cluster's OIDC issuer as a federated credential subject with a Kubernetes service account annotated with the app's client ID, giving pods secretless Azure AD tokens.

**Why the others are wrong:**
- A cluster-level system-assigned identity can't be scoped to individual pods, and storing a secret contradicts the goal.
- Managed identities cannot be attached directly to pods, and using a stored secret defeats the purpose.
- This relies on certificate/secret-based auth, not federation, and does not eliminate stored credentials.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** A shared automation solution running across multiple Azure Automation accounts needs a single identity with consistent permissions pre-configured before any automation account is created. Which should you select?

A) System-assigned managed identity
B) User-assigned managed identity
C) Workload identity federation
D) Certificate-based service principal

<details>
<summary>Answer</summary>

**Correct: B**

User-assigned managed identities exist independently of any resource and can be pre-created, then attached to multiple Automation accounts with consistent RBAC.

**Why the others are wrong:**
- System-assigned identities cannot exist before their resource is created and are strictly 1:1.
- Workload identity federation targets external non-Azure workloads (GitHub, Kubernetes), not native Azure resource-to-resource identity sharing.
- Certificate-based service principals require manual certificate management and rotation.

</details>

---

**Q5.** Which identity solution eliminates the need to manage or rotate any credential value, is automatically handled by Azure AD, and can only be assigned to a single Azure resource with a matching lifecycle?

A) User-assigned managed identity
B) System-assigned managed identity
C) Service principal with federated credential
D) Enterprise application with client secret

<details>
<summary>Answer</summary>

**Correct: B**

System-assigned managed identities are automatically created and destroyed with exactly one resource, with credentials fully managed by Azure AD.

**Why the others are wrong:**
- User-assigned identities can be attached to multiple resources and have their own independent lifecycle, not matching a single resource.
- Federated credentials are designed for external workloads outside Azure, not automatic 1:1 resource lifecycle binding.
- Enterprise applications with client secrets require manual secret storage and rotation.

</details>

---

**Q6.** When configuring a federated credential for a GitHub Actions workflow that should trigger only on pushes to the 'main' branch, which subject identifier format should you use?

A) repo:org/repo:environment:main
B) repo:org/repo:pull_request
C) repo:org/repo:ref:refs/tags/main
D) repo:org/repo:ref:refs/heads/main

<details>
<summary>Answer</summary>

**Correct: D**

The ref:refs/heads/<branch> subject format matches a workflow run triggered by a push to that specific branch.

**Why the others are wrong:**
- The environment: subject format is used for GitHub Environments, not branch pushes.
- The pull_request subject matches pull request events, not branch pushes.
- The refs/tags/ format matches tag pushes, not the branch head.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** You are configuring least-privilege RBAC for a managed identity that only needs to read blobs from a single storage container. Which role assignment approach is correct?

A) Assign 'Storage Blob Data Contributor' at the subscription scope
B) Assign 'Storage Blob Data Reader' scoped to the specific container
C) Assign 'Owner' scoped to the storage account
D) Assign 'Contributor' scoped to the resource group

<details>
<summary>Answer</summary>

**Correct: B**

This grants only read access to blob data and scopes it to the narrowest resource, meeting least-privilege requirements exactly.

**Why the others are wrong:**
- Contributor grants write/delete permissions beyond read-only need, and subscription scope is far too broad.
- Owner grants full control including RBAC management, vastly exceeding what's required.
- Contributor at resource group scope allows managing all resources in the RG, not just data reads on one container.

</details>

---

**Q8.** What is the primary security advantage of workload identity federation compared to using a stored client secret or certificate for a service principal?

A) It removes the need to store, rotate, or protect any long-lived credential value in the external system
B) It provides faster token issuance than certificate-based authentication
C) It automatically grants Global Administrator access to the workload
D) It allows the workload to bypass Conditional Access policies

<details>
<summary>Answer</summary>

**Correct: A**

Federation exchanges a short-lived external OIDC token for an Azure AD token, so no secret or certificate ever needs to be stored or rotated by the external system.

**Why the others are wrong:**
- Token issuance speed is not the tested or accurate advantage.
- Federation does not grant any elevated privilege by default; RBAC assignments still control access.
- Conditional Access policies still apply to token requests from federated identities.

</details>

---

