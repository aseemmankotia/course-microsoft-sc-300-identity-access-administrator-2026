# Practice Test 2: SC-300: Microsoft Identity and Access Administrator Prep

- **Questions:** 42
- **Time limit:** 90 minutes
- **Passing score:** 70%%

> Answers are in `answer-key-2.md`. Track results in `score-tracker.md`.

---

**Q1.** Contoso currently uses federated authentication (AD FS) for all 50,000 users. IT wants to migrate to Microsoft Entra Connect with Password Hash Sync and evaluate the impact on a pilot group of 200 users in the Sales department before cutting the entire directory over, without modifying the existing federation trust. What should they configure?

A) Enable Seamless SSO on the on-premises AD FS servers and monitor sign-in logs
B) Create a Staged Rollout feature in Microsoft Entra ID, enable Password Hash Sync and Seamless SSO, and add the Sales security group to the feature
C) Run Set-MsolDomainAuthentication to convert the entire domain from federated to managed immediately
D) Deploy Pass-through Authentication agents only on the workstations of the pilot users

---

**Q2.** Fabrikam wants to collaborate with users from partner organization Adatum inside a Microsoft Teams shared channel. Adatum users must authenticate with their own Adatum credentials, and no guest user object should be created in Fabrikam's tenant. Both organizations must configure mutual cross-tenant trust settings for this to work. Which capability should be used?

A) Microsoft Entra B2B direct connect
B) Microsoft Entra B2B collaboration invitation
C) Microsoft Entra External ID for customers (B2C)
D) Azure AD Application Proxy

---

**Q3.** Contoso's identity admin must ensure that Global Administrators cannot reset passwords or edit profile attributes for the CEO and board members' accounts, even though those admins retain their tenant-wide role elsewhere. Only members of the role-assignable 'Executive Support' group should be able to manage these specific accounts. What should be configured?

A) Assign the Privileged Role Administrator role to the Executive Support group at the tenant scope
B) Create a restricted management administrative unit containing the executive accounts, and assign the Helpdesk Administrator role scoped to that unit to the Executive Support group
C) Create a Conditional Access policy that blocks Global Administrator sign-ins from managing executive mailboxes
D) Add the executive accounts to a dynamic security group that is excluded from all directory role assignments

---

**Q4.** An organization wants users to reset their on-premises Active Directory password through Microsoft Entra self-service password reset (SSPR), with the new password written back to on-premises AD in near real time. Which combination is required to make this work?

A) Password Hash Sync only, with a Microsoft Entra ID Free tier license
B) The Microsoft Entra Connect Health agent installed on all domain controllers
C) Microsoft Entra Connect with password writeback enabled, a Microsoft Entra ID P1 or higher license, and SSPR configured
D) Pass-through Authentication agents configured with a writeback extension

---

**Q5.** After configuring Microsoft Entra Connect with Password Hash Sync, synchronization fails for two on-premises user accounts with the error 'Attribute proxyAddresses or userPrincipalName must be unique across the directory.' Investigation shows both AD accounts were accidentally assigned the same email-based value during a migration. Which Microsoft Entra Connect feature automatically appends a temporary suffix to one of the conflicting values so synchronization can proceed while the source data issue is fixed?

A) Duplicate Attribute Resiliency
B) Sync Rules Editor conflict resolution
C) Connector space full import
D) Export Deletion Threshold

---

**Q6.** A user is a member of two groups: one assigns a Microsoft 365 E3 license (which includes Intune and EMS service plans), and another assigns a standalone Enterprise Mobility + Security E3 license whose service plans conflict with plans already granted by the M365 E3 license. The Microsoft Entra admin center shows a licensing 'Problem' status for the user. What is the recommended way to resolve the conflict while keeping the user in both groups for other purposes, such as Conditional Access targeting?

A) Remove the user from both groups and assign both licenses to the user directly
B) Delete the standalone Enterprise Mobility + Security E3 license from the tenant's subscriptions entirely
C) Assign the user the Global Administrator role so that Microsoft Entra bypasses license conflict checks
D) In the group's license assignment, use 'Assign options' to disable the specific conflicting service plan for that group's license

---

**Q7.** Contoso requires that user passwords are validated directly against on-premises Active Directory and must never be stored or synchronized to Microsoft Entra ID in any form. The solution must also provide high availability without deploying AD FS servers. Which authentication method should be configured?

A) Password Hash Synchronization
B) Federation with AD FS
C) Seamless Single Sign-On only
D) Pass-through Authentication with multiple PTA agents installed on separate on-premises servers

---

**Q8.** An HR team needs to manage HR department user objects, but the security team requires that even Global Administrators be prevented from modifying or resetting passwords for these users unless explicitly assigned a role scoped to the HR object container. Which feature satisfies this requirement?

A) Dynamic administrative unit with rule-based membership
B) Custom role with reduced permissions assigned at tenant scope
C) Restricted management administrative unit
D) Conditional Access policy scoped to HR group

---

**Q9.** A company's on-premises AD has an OU containing both regular user accounts that must sync to Microsoft Entra ID and several disabled legacy service accounts that must be excluded. All accounts share the same OU, so OU-based filtering cannot separate them. Which Microsoft Entra Connect configuration should be used to exclude only the disabled service accounts?

A) OU-based filtering only
B) Attribute-based filtering using synchronization rule editor
C) Domain-based filtering
D) Group-based filtering (Microsoft Entra Connect cloud sync group scoping)

---

**Q10.** Two partner organizations want their employees to collaborate in the same Microsoft Teams shared channels while accessing each other's tenant resources, but neither organization wants guest user objects created in its own directory for the partner's employees. Which capability should be configured between the two tenants?

A) B2B collaboration with guest invitations
B) Azure AD B2C custom policies
C) B2B direct connect
D) Cross-tenant synchronization

---

**Q11.** A security team wants to eliminate standing access to the Global Administrator role. They require that: (1) no one holds the role permanently, (2) activation requires approval from a designated security officer, (3) Azure AD (Entra) MFA must be performed at the moment of activation, and (4) activations automatically expire after 8 hours. Which PIM configuration satisfies ALL of these requirements?

A) Assign the role as Active with a permanent expiration date and require justification only
B) Assign the role as Eligible and configure an Access Review to run every 8 hours
C) Assign the role as Active, disable approval, and rely on Conditional Access sign-in frequency of 8 hours
D) Assign the role as Eligible, enable 'Require approval to activate', enable 'Require Microsoft Entra multifactor authentication', and set maximum activation duration to 8 hours

---

**Q12.** An organization creates a custom Conditional Access authentication strength that must exclude SMS, voice call, and Microsoft Authenticator push notifications, allowing only credentials resistant to phishing. Which built-in authentication strength already meets this requirement without customization?

A) Multifactor authentication strength
B) Passwordless MFA strength
C) Phishing-resistant MFA strength
D) MFA strength

---

**Q13.** Microsoft Entra ID Protection flags a user with 'High' user risk due to a leaked credentials detection. A Conditional Access user risk policy is configured to require a secure password change for high-risk users, but the affected user has never registered for SSPR and cannot complete the remediation. What should the administrator do FIRST?

A) Manually dismiss the risk in Identity Protection without further action to unblock the user immediately
B) Verify the user's identity out-of-band, then have them register authentication methods, and only dismiss the risk after confirming a secure sign-in
C) Delete the user account and recreate it with a new UPN to clear the risk state
D) Disable the user risk Conditional Access policy tenant-wide until SSPR rollout is complete

---

**Q14.** A company has hybrid Azure AD joined Windows devices and wants to deploy Windows Hello for Business without standing up or maintaining an on-premises PKI, and without requiring Windows Server 2016+ domain controllers for key trust. Which deployment model should they choose?

A) Hybrid Cloud Trust
B) Hybrid Certificate Trust
C) Hybrid Key Trust
D) On-premises Key Trust

---

**Q15.** A company onboards external contractors who use only personal Android and iOS phones (no Windows devices, no hardware security keys) and wants them to authenticate without ever entering a password. Which authentication method should the administrator enable and enforce via the Authentication Methods policy?

A) Windows Hello for Business
B) Temporary Access Pass
C) Microsoft Authenticator passwordless phone sign-in
D) FIDO2 security key

---

**Q16.** An administrator is asked to explain the core benefit of Continuous Access Evaluation (CAE) compared to traditional Conditional Access session enforcement based purely on token lifetime. Which statement correctly describes this benefit?

A) CAE issues access tokens that never expire, removing the need for session controls
B) CAE re-evaluates critical events (such as user account disablement, password reset, or location change) in near real time instead of waiting for the access token to expire
C) CAE replaces the need for multifactor authentication entirely
D) CAE only applies to conditional access policies targeting Exchange Online mailboxes

---

**Q17.** Your organization requires that activation of the Global Administrator role in Privileged Identity Management (PIM) always requires manager approval, must include a written justification, and cannot remain active for longer than 4 hours. Which PIM configuration meets all these requirements?

A) In the role settings for Global Administrator, enable "Require approval to activate," enable "Require justification on activation," and set Maximum activation duration to 4 hours
B) Enable PIM for Groups and assign the Global Administrator role to the group with a 4-hour membership duration
C) Configure a Conditional Access policy that blocks Global Administrator activation from outside the corporate network and requires MFA
D) Enable "Require Microsoft Entra Multifactor Authentication" and "Require justification on activation," leaving Maximum activation duration at the default of 8 hours

---

**Q18.** You configure Microsoft Entra ID Protection risk policies. You need a Conditional Access policy that forces users to change their password immediately when Identity Protection detects that their credentials have likely been compromised. Which risk condition should the policy use?

A) User risk
B) Sign-in risk
C) Device risk
D) Location risk

---

**Q19.** A company is migrating from the legacy per-user MFA and SSPR settings to the unified Authentication methods policy in Microsoft Entra ID. The identity team wants new hires to receive a time-limited passcode they can use once to sign in and register for Windows Hello for Business, without having a password on day one. Which authentication method should be enabled in the Authentication methods policy?

A) Software OATH token
B) SMS-based authentication
C) Certificate-based authentication
D) Temporary Access Pass

---

**Q20.** You configure a Conditional Access policy for unmanaged devices accessing a sensitive SaaS application. You need users to be prompted to sign in again every time they close and reopen the browser, even if their access token has not expired. Which session control should you configure?

A) Persistent browser session set to "Never persistent"
B) Sign-in frequency set to periodic reauthentication every 1 hour
C) Cloud App Security conditional access app control
D) Customize continuous access evaluation

---

**Q21.** A company has hybrid Microsoft Entra joined Windows devices across branch offices with unreliable WAN links to on-premises domain controllers. They have no PKI infrastructure and want to deploy Windows Hello for Business so users can sign in with a PIN or biometrics even when connectivity to a domain controller is limited after enrollment. Which Windows Hello for Business trust model should they deploy?

A) Hybrid certificate trust
B) On-premises key trust
C) Hybrid key trust
D) Cloud Kerberos trust

---

**Q22.** An administrator is deciding between using a standard "Require multifactor authentication" grant control and applying the built-in "Phishing-resistant MFA" Authentication strength in a Conditional Access policy for admin sign-ins. What is the key difference?

A) Authentication strength enforces specific combinations of authentication methods, such as FIDO2 or certificate-based authentication, while the standard MFA grant accepts any registered MFA method equally
B) They are functionally identical and fully interchangeable in every scenario
C) Authentication strength can only be applied to guest users, while the standard MFA grant applies only to member accounts
D) The standard MFA grant control supports FIDO2 security keys, but Authentication strength does not support FIDO2

---

**Q23.** A DevOps team configures a federated credential on an app registration to allow a GitHub Actions workflow to authenticate to Azure without a client secret. Deployments to production must ONLY be triggered by a push to the 'main' branch — pull request builds and other branches must not be able to use this credential. Which subject identifier should be configured on the federated credential?

A) repo:contoso-org/deploy-repo:environment:production
B) repo:contoso-org/deploy-repo:pull_request
C) repo:contoso-org/deploy-repo:ref:refs/tags/v1.0
D) repo:contoso-org/deploy-repo:ref:refs/heads/main

---

**Q24.** A company's security team mandates that no long-lived secrets exist in any CI/CD pipeline configuration. GitHub Actions workflows currently authenticate to Azure using a stored client secret that must be manually rotated every 90 days. Which change eliminates the stored secret while still allowing the workflow to authenticate?

A) Create a new client secret with a 2-year expiration and store it as an encrypted GitHub Actions secret
B) Configure a federated credential on the app registration trusting GitHub's OIDC issuer, then remove all client secrets from the app registration
C) Upload a certificate credential to the app registration and store the private key file as a GitHub Actions secret
D) Create a service account with a personal access token and grant it Owner role on the subscription

---

**Q25.** A Security Operations team wants Microsoft Entra ID Protection to automatically flag service principals whose credentials appear on the dark web (leaked credentials) and to detect service principals signing in with anomalous properties, then apply Conditional Access to block those risky sign-ins. Which license is specifically required to enable risk detection and Conditional Access for these non-human identities?

A) Microsoft Entra Workload ID Premium
B) Microsoft Entra ID P1
C) Microsoft Defender for Cloud Apps
D) Microsoft Entra ID P2

---

**Q26.** An organization needs a single managed identity to be assigned to 15 Azure VMs so they can all access the same Key Vault. VMs are frequently decommissioned and recreated, and the identity's Key Vault access policy must NOT be affected when individual VMs are deleted. Which identity type meets this requirement?

A) A user-assigned managed identity created independently and assigned to each of the 15 VMs
B) A system-assigned managed identity enabled on one 'primary' VM and referenced by the other 14
C) A service principal with a client secret stored in each VM's configuration
D) An app registration with a certificate credential installed on each VM

---

**Q27.** Contoso develops a multi-tenant SaaS application and registers it as an app registration in the Contoso Microsoft Entra tenant. An administrator at Fabrikam grants admin consent for the app to access Fabrikam's directory data. What object is created in Fabrikam's tenant as a result of this consent?

A) A new app registration owned and editable by Fabrikam administrators
B) A full copy of Contoso's app registration object, including its manifest and API permissions definitions
C) A service principal (enterprise application) representing Contoso's app, scoped to Fabrikam's tenant
D) No object is created; consent grants are tracked only within Contoso's tenant

---

**Q28.** A tenant administrator discovers that any user in the organization can register new app registrations, creating governance gaps around ownership of workload identities. The administrator wants only a specific security-vetted group to be able to create new app registrations going forward. What is the default value of the relevant tenant setting, and what should the administrator do?

A) The setting defaults to 'No'; enable the Application Developer role for all users to allow controlled registration
B) The setting 'Users can register applications' defaults to 'Yes'; set it to 'No' and assign the Application Developer role to the specific users or group that need to register apps
C) The setting defaults to 'Yes' with no way to restrict it; the administrator must rely on Privileged Identity Management instead
D) The setting defaults to 'No' and cannot be changed; a custom RBAC role must be created at the subscription level

---

**Q29.** You configure a federated identity credential on an Entra ID app registration so that a workload running in an AKS pod can authenticate without secrets. The issuer is set to the AKS cluster's OIDC issuer URL. Which value must you configure as the 'subject' so it matches the token presented by the workload?

A) The tenant ID of the Microsoft Entra ID directory
B) The Application (client) ID of the app registration
C) The Kubernetes service account formatted as system:serviceaccount:<NAMESPACE>:<SERVICE_ACCOUNT_NAME>
D) The resource ID of the AKS cluster

---

**Q30.** A Virtual Machine Scale Set (VMSS) scales between 2 and 50 instances based on load. All instances must use the exact same identity, with consistent permissions on Azure Key Vault, and that identity must not be deleted when instances scale in or are individually removed. Which identity configuration meets these requirements?

A) Enable a system-assigned managed identity on the VMSS so each instance receives its own identity automatically
B) Create a user-assigned managed identity once and assign it to the VMSS so all instances share it
C) Create an app registration with a client secret and distribute the secret to every instance
D) Enable a system-assigned managed identity on each VM instance individually as it is provisioned

---

**Q31.** The security team mandates that a GitHub Actions pipeline deploying to Azure must authenticate without storing any long-lived secret or certificate in pipeline configuration. Which configuration meets this requirement?

A) Create a service principal with a client secret valid for 24 months and store it as an encrypted GitHub secret
B) Enable a system-assigned managed identity directly on the app registration used by the pipeline
C) Configure a federated identity credential on the app registration that trusts GitHub Actions OIDC tokens for the specific repository and branch
D) Create a service principal with a certificate credential and store the private key as an encrypted GitHub secret

---

**Q32.** A Global Administrator wants a Conditional Access policy that blocks a specific service principal from authenticating unless the request originates from an already-configured named location representing the corporate network. Which policy configuration correctly achieves this using Conditional Access for workload identities?

A) Scope the policy to the service principal, set Locations condition to the corporate named location, and set grant control to Require multifactor authentication
B) Scope the policy to all users and groups, set Locations condition to the corporate named location, and set grant control to Require multifactor authentication
C) Scope the policy to the service principal, set Locations condition to all locations except the corporate named location, and set grant control to Block access
D) Scope the policy to the service principal, set Locations condition to the corporate named location, and set grant control to Require compliant device

---

**Q33.** An organization uses Microsoft Entra entitlement management. They want to prevent any user who already has the 'Finance-Sensitive' access package from also being granted the 'Marketing-External' access package, due to a conflict-of-interest policy, without requiring manual review of every request. Which feature should be configured?

A) Configure an access review with auto-apply on the 'Marketing-External' access package
B) Configure separation of duties for the access package, specifying 'Finance-Sensitive' as the incompatible package
C) Require terms of use acceptance before requesting 'Marketing-External'
D) Set an expiration policy on the 'Finance-Sensitive' access package assignment

---

**Q34.** A company wants a lifecycle workflow to run automatically and immediately whenever a user's employeeType attribute value changes from 'Employee' to 'Contractor', rather than waiting for the next scheduled execution. Which trigger type should the workflow use?

A) Attribute changed trigger
B) Time-based (scheduled) trigger
C) On-demand trigger
D) Employee mover template trigger

---

**Q35.** An administrator creates a recurring access review for members of a role that is eligible in PIM. The administrator wants the review's outcome (removing denied users) to be implemented automatically once the review period ends, without requiring anyone to manually apply the results. Which setting accomplishes this?

A) Require reviewers to provide a reason for every decision
B) Configure a multi-stage review with two sequential reviewers
C) Disable the option allowing reviewers to review their own access
D) Enable 'Auto apply results to resource' when configuring the access review

---

**Q36.** A compliance requirement states that all users must re-accept a specific Terms of Use policy every 90 days, even if they accepted the current version previously. Which Terms of Use configuration satisfies this requirement without publishing a new document version each time?

A) Configure the 'Expire consents' setting on the terms of use policy to 90 days
B) Enable per-device enforcement of the terms of use
C) Increment the terms of use document version number and display name
D) Add a Conditional Access grant control requiring terms of use

---

**Q37.** An organization wants employees to be able to consent to apps that request only low-impact permissions such as sign-in and basic profile read, while blocking consent for apps requesting high-impact permissions like full mailbox access — without turning off user consent entirely. Which configuration meets this requirement?

A) Set the user consent setting to 'Do not allow user consent'
B) Set the user consent setting to 'Allow user consent for all apps'
C) Enable the admin consent workflow for all app permission requests
D) Set user consent to 'Allow user consent for apps from verified publishers, for selected permissions' and classify the low-impact permissions accordingly

---

**Q38.** A company requires that requests for a specific access package go through two sequential levels of approval — first a manager, then a resource owner — before access is granted. Which capability supports this requirement?

A) Configure PIM role assignment approval with multiple approvers on the eligible assignment
B) Configure the access package policy with a two-stage approval process, specifying different approvers for each stage
C) Configure an access review with a two-stage decision process
D) Add a Conditional Access approval workflow to the access package

---

**Q39.** A company uses Microsoft Entra ID Governance Lifecycle Workflows to manage the leaver process. When an employee's termination date arrives, the workflow must disable the account, remove group memberships, AND trigger a custom on-premises HR system update via an existing Azure Logic App that performs additional cleanup tasks not natively supported by Lifecycle Workflows. Which capability should the identity administrator configure to invoke the Logic App as part of the workflow?

A) Add a Run a Function task using an Azure Automation runbook
B) Create a Conditional Access policy that triggers the Logic App when the account is disabled
C) Use an Access Review with auto-apply set to call the Logic App webhook on denial
D) Configure a custom task extension that calls the Logic App via a Logic App connector in the workflow

---

**Q40.** An organization uses entitlement management with two access packages in the same catalog: 'Finance-Auditor' and 'Finance-Approver.' Compliance requires that no user can hold both access packages at the same time due to separation-of-duties requirements. The administrator wants Microsoft Entra to automatically prevent a user from requesting 'Finance-Approver' if they already have an active assignment to 'Finance-Auditor.' Which feature should be configured?

A) Create an access review on both access packages with a manager as reviewer
B) Configure a Conditional Access policy that blocks sign-in when both roles are assigned
C) Set a lifecycle workflow to remove 'Finance-Auditor' automatically when 'Finance-Approver' is requested
D) Enable an incompatible access package setting on the 'Finance-Approver' access package pointing to 'Finance-Auditor'

---

**Q41.** A company runs a recurring quarterly access review on guest users in several Teams-connected Microsoft 365 groups. Reviewers are the group owners. The company wants any guest whose access is not reviewed by the deadline to automatically have their group membership removed, without an administrator manually applying the results. Which setting combination on the access review achieves this?

A) Set 'Reviewers' to 'Members (self-review)' and enable 'Show recommendations'
B) Enable 'Auto apply results to resource' and set 'If reviewers don't respond' to 'Remove access'
C) Enable 'Require reason on approval' and set the review duration to 30 days
D) Set 'Auto apply results to resource' to disabled and configure a Logic App to remove access manually

---

**Q42.** A security team wants regular employees to be able to request admin consent for third-party applications that require high-privilege permissions, since users cannot consent to these permissions themselves. Requests must be routed to a specific security group of designated reviewers who can approve or deny the request from within Microsoft Entra ID, and requesting users must automatically be notified of the outcome. Which feature should be configured?

A) Permission classification, marking the required permissions as 'Low impact'
B) User consent settings, changing the policy to 'Allow user consent for apps from verified publishers'
C) Admin consent workflow, enabled with the reviewer security group assigned as reviewers
D) App registration ownership, adding the requesting users as owners of the application

---

