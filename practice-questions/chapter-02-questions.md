## Chapter 2: External Identities & Hybrid Identity Synchronization — Practice Questions

**Q1.** A company has strict compliance rules stating that no password data of any kind, hashed or otherwise, may ever leave the on-premises datacenter, and they cannot deploy additional on-prem servers due to a hardware freeze. AD FS is not an option because they lack the infrastructure team to maintain a farm. Which authentication method should they choose?

A) Pass-through Authentication (PTA) with a single lightweight agent
B) Password Hash Synchronization (PHS)
C) Federation with AD FS
D) Seamless SSO only, with no other authentication method

<details>
<summary>Answer</summary>

**Correct: A**

PTA validates credentials directly against on-prem AD in real time via a lightweight agent; no password or hash is ever stored in the cloud, satisfying the compliance requirement without a new farm.

**Why the others are wrong:**
- PHS synchronizes a hash of the password hash to Entra ID — this violates the 'no password data leaves the datacenter' rule.
- Federation requires a full AD FS farm plus WAP servers, which contradicts the stated infrastructure constraint.
- Seamless SSO is not an authentication method by itself — it only removes sign-in prompts and must be paired with PHS or PTA.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** Contoso and Fabrikam need their employees to collaborate directly in Microsoft Teams shared channels using their own home tenant identities, without either company creating guest user objects in their own directory. What should be configured?

A) B2B collaboration with guest invitations sent to all Fabrikam users
B) A single Entra ID tenant merge between Contoso and Fabrikam
C) External collaboration settings set to 'Anyone in the organization can invite guests'
D) B2B direct connect with mutual cross-tenant access trust enabled

<details>
<summary>Answer</summary>

**Correct: D**

B2B direct connect is purpose-built for Teams shared channels; it establishes a mutual, two-way trust between tenants via cross-tenant access settings, and users retain their home-tenant identity with no guest object created locally.

**Why the others are wrong:**
- B2B collaboration always creates a guest object in the resource tenant's directory, which the requirement explicitly excludes.
- Tenant merging is not a supported or realistic solution for cross-company Teams collaboration.
- External collaboration settings only govern who can send B2B collaboration invitations, not B2B direct connect trust.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** An admin needs to migrate a Microsoft Entra Connect sync server to new hardware without risking duplicate exports to Microsoft Entra ID or on-premises AD during the cutover. What should the admin configure on the new server before promoting it?

A) Password writeback disabled
B) Staging mode enabled
C) A new custom sync rule that filters all objects
D) Seamless SSO enabled on the new server only

<details>
<summary>Answer</summary>

**Correct: B**

Staging mode lets a second server run with identical configuration, importing and running sync cycles, but suppresses exports to AD and Entra ID until an admin disables staging mode to promote it — enabling a safe, zero-downtime cutover.

**Why the others are wrong:**
- Disabling password writeback only stops one specific export feature, not full duplicate sync/export risk.
- Filtering all objects would just prevent any sync from occurring, not enable a safe parallel run for testing.
- Seamless SSO configuration is unrelated to preventing duplicate exports during a server migration.

</details>

---

**Q4.** Which Microsoft Entra ID feature should be used to synchronize identities from multiple AD forests using lightweight, cloud-managed agents when there is no requirement for device writeback or complex synchronization rule customization?

A) Microsoft Entra Connect (full sync engine)
B) AD FS with Web Application Proxy
C) Microsoft Entra Cloud Sync
D) B2B direct connect

<details>
<summary>Answer</summary>

**Correct: C**

Cloud Sync uses small, cloud-orchestrated provisioning agents ideal for simple multi-forest scenarios and requires far less on-prem footprint than full Entra Connect, though it only supports PHS for authentication.

**Why the others are wrong:**
- Entra Connect handles complex multi-forest topologies well but is heavier and requires more configuration than needed here.
- AD FS/WAP is for federated sign-in, not directory synchronization.
- B2B direct connect is for cross-tenant collaboration, not on-prem-to-cloud identity sync.

</details>

---

**Q5.** An organization wants to allow another organization's Conditional Access MFA claims to be trusted when their users access shared resources, without disabling MFA enforcement entirely. Where is this configured?

A) External collaboration settings, guest invite restrictions
B) Microsoft Entra Connect, sync scoping filters
C) Cross-tenant access settings, inbound trust settings
D) Conditional Access named locations

<details>
<summary>Answer</summary>

**Correct: C**

Inbound trust settings under Cross-tenant access settings let a tenant trust MFA, compliant device, and hybrid-joined device claims performed in a user's home tenant, avoiding redundant MFA prompts.

**Why the others are wrong:**
- External collaboration settings control who can send invitations, not claim trust.
- Sync scoping filters control which on-prem objects sync to the cloud, unrelated to cross-tenant trust.
- Named locations define network-based Conditional Access conditions, not cross-tenant claim trust.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** By default, how frequently does Microsoft Entra Connect synchronize password hashes to Microsoft Entra ID once PHS is enabled, independent of the standard delta sync cycle?

A) Every 2 minutes
B) Every 30 minutes
C) Every 24 hours
D) Only on manual trigger via PowerShell

<details>
<summary>Answer</summary>

**Correct: A**

After the initial full password hash sync, Entra Connect checks for changed password hashes and synchronizes them every 2 minutes, independent of the 30-minute default delta sync cycle for other attributes.

**Why the others are wrong:**
- 30 minutes is the default delta sync cycle for general object/attribute sync, not password hash sync specifically.
- 24 hours is not a default interval used anywhere in Entra Connect sync scheduling.
- Sync happens automatically on schedule; manual triggering is possible but not the default behavior.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** How many Pass-through Authentication agents does Microsoft recommend deploying for high availability in a production environment?

A) 1, since only one agent can be active at a time
B) 2, matching the primary/secondary domain controller model
C) 5, one per Active Directory site
D) 3, for redundancy and load balancing across on-prem servers

<details>
<summary>Answer</summary>

**Correct: D**

Microsoft's official recommendation is at least 3 PTA agents installed on separate on-prem servers for redundancy and load balancing; only 1 is the technical minimum requirement.

**Why the others are wrong:**
- 1 agent works but is not the recommended production configuration and creates a single point of failure.
- There is no primary/secondary agent model — all agents can serve authentication requests concurrently.
- 5 agents per site is not a Microsoft guideline; the recommendation is a flat count of 3, not tied to site topology.

</details>

---

**Q8.** What underlying authentication protocol does Microsoft Entra Seamless Single Sign-On rely on to silently authenticate domain-joined users?

A) SAML 2.0
B) Kerberos
C) OAuth 2.0 client credentials flow
D) NTLM v1

<details>
<summary>Answer</summary>

**Correct: B**

Seamless SSO creates a computer object (AZUREADSSOACC) in on-prem AD holding a Kerberos decryption key; domain-joined devices use Kerberos tickets to silently prove identity to Entra ID.

**Why the others are wrong:**
- SAML is used in federation scenarios (AD FS), not Seamless SSO.
- OAuth 2.0 client credentials flow is used for app-to-app authentication, not user SSO.
- NTLM is not used by Seamless SSO; it relies specifically on Kerberos.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

