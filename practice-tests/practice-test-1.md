# Practice Test 1: SC-300: Microsoft Identity and Access Administrator Prep

- **Questions:** 42
- **Time limit:** 90 minutes
- **Passing score:** 70%%

> Answers are in `answer-key-1.md`. Track results in `score-tracker.md`.

---

**Q1.** A company has helpdesk staff in three regional offices. The Global Administrator wants each regional helpdesk team to be able to reset passwords and manage licenses only for the users in their own region, without granting rights over users in other regions. Which feature should be configured to scope these administrative rights?

A) Custom domains
B) Dynamic groups
C) Administrative units
D) Conditional Access

---

**Q2.** A manufacturing company wants to give employees at a partner supplier organization access to a shared SharePoint site using the partner employees' existing corporate credentials, without the company having to create or manage separate accounts for them. Which feature should be used?

A) Microsoft Entra External ID for customers
B) Microsoft Entra B2B collaboration
C) Self-service password reset
D) Microsoft Entra B2C

---

**Q3.** An organization implements Microsoft Entra Connect with password hash synchronization. Assuming default settings are unchanged, how frequently does the sync engine synchronize changes from on-premises Active Directory to Microsoft Entra ID?

A) 5 minutes
B) 30 minutes
C) 2 hours
D) 24 hours

---

**Q4.** A company is retiring its on-premises AD FS federation servers and wants the simplest hybrid authentication method that requires no additional on-premises authentication agents beyond the Microsoft Entra Connect sync server, while still supporting Conditional Access and leaked credential detection in the cloud. Which authentication method should they choose?

A) Pass-through Authentication
B) Federation with AD FS
C) Password hash sync
D) Seamless SSO only

---

**Q5.** Which statement correctly describes Microsoft Entra Connect cloud sync compared to the traditional Microsoft Entra Connect Sync (Azure AD Connect) engine?

A) Cloud sync requires SQL Server Standard edition installed on-premises for object filtering
B) Cloud sync supports federation with AD FS as an authentication method
C) Cloud sync uses lightweight provisioning agents and is managed entirely from the Microsoft Entra admin center, supporting multiple on-premises AD forests without needing a full sync engine on-premises
D) Cloud sync replaces Conditional Access policies for hybrid identity

---

**Q6.** A company assigns Microsoft 365 E3 licenses to users via group-based licensing. Several users who still have mailboxes hosted on-premises in an Exchange hybrid deployment show a license error in the Microsoft Entra admin center for the Exchange Online service plan, even though other service plans in the same license activate successfully. What is the MOST likely cause of this error?

A) The Exchange Online service plan conflicts because the users' on-premises hybrid mailbox attributes prevent proper cloud provisioning until mailbox migration completes
B) The group has exceeded the 50,000 member limit for group-based licensing
C) The group is a dynamic device group instead of a dynamic user group
D) The users are missing a UsageLocation attribute

---

**Q7.** A company's Microsoft Entra tenant has a Global Administrator who manages 40,000 users across five business units. The security team wants regional IT leads to reset passwords and manage licenses only for users in their own business unit, without granting them rights to any other business unit's users. What should you implement?

A) Assign the Password Administrator role at the tenant level to each regional IT lead
B) Create a custom role and assign it using Privileged Identity Management with permanent eligible assignments
C) Move each business unit into a separate Microsoft Entra tenant and configure a cross-tenant sync
D) Create administrative units scoped to each business unit and assign the User Administrator role to each regional IT lead scoped to their administrative unit

---

**Q8.** A manufacturing company needs to give employees at a partner organization access to a specific SharePoint site and a Teams channel. The partner's users must sign in using their own existing corporate Microsoft Entra credentials, and the company must not need to create or manage separate accounts or credentials for these users. Which capability should be used?

A) Microsoft Entra External ID for customers (B2C) with local accounts
B) A one-way forest trust between the company's on-premises AD and the partner's on-premises AD
C) Create synced accounts for the partner users using Microsoft Entra Connect with a filtered OU
D) Microsoft Entra B2B collaboration with the partner as a Microsoft Entra tenant identity provider

---

**Q9.** An organization uses Microsoft Entra Connect with Password Hash Synchronization for hybrid identity. Security policy requires that when an administrator disables a user's on-premises Active Directory account, the user must be immediately blocked from signing in to Microsoft 365, without waiting for the next synchronization cycle. Which change should be made?

A) Enable seamless single sign-on in addition to Password Hash Synchronization
B) Reduce the Microsoft Entra Connect sync cycle interval from 30 minutes to 5 minutes
C) Switch the sign-in method from Password Hash Synchronization to Pass-through Authentication
D) Enable federation with AD FS instead of Password Hash Synchronization

---

**Q10.** An administrator uses group-based licensing to assign a Microsoft 365 E5 license to a security group. A user in that group is also a member of a second group that assigns a Microsoft 365 E3 license. The E5 license includes a service plan for Microsoft Defender for Office 365, but the E3 license does not include an equivalent conflicting plan. What is the expected licensing outcome for this user?

A) The user's license assignment enters an error state and no licenses are applied until the conflict is manually resolved
B) Both licenses are applied successfully, and the user receives the combined set of service plans from both licenses
C) Only the most recently assigned license is applied, and the other license is automatically removed
D) Microsoft Entra ID automatically disables the Defender for Office 365 service plan to prevent duplication

---

**Q11.** A manufacturing company has shared kiosk workstations on the factory floor. Multiple workers use the same physical device throughout the day, and each worker needs to sign in with a passwordless credential that they can carry with them between kiosks. Which authentication method should the identity administrator deploy?

A) Windows Hello for Business (device-bound biometric/PIN credential)
B) FIDO2 security keys
C) Temporary Access Pass
D) Certificate-based authentication

---

**Q12.** A company requires users signing in from unmanaged devices to reauthenticate every hour, while users on Microsoft Entra hybrid joined compliant devices should not be interrupted. Which Conditional Access session control configuration meets this requirement?

A) Configure Sign-in frequency to 'Periodic reauthentication' every 1 hour, scoped with a device filter to exclude compliant devices
B) Configure a Conditional Access session control for Persistent browser session set to 'Never persistent'
C) Enable Conditional Access App Control with app-enforced restrictions
D) Set the Conditional Access grant control to 'Require multifactor authentication' for all users

---

**Q13.** A security team wants every activation of the eligible Global Administrator role in Microsoft Entra PIM to require multifactor authentication, approval from a designated approver, and a justification comment from the requesting user. Which single set of role settings satisfies this requirement?

A) On the Assignment tab, set Assignment type to Active and Assignment duration to Permanent
B) On the Activation tab, enable 'Require Azure AD Multifactor Authentication,' enable 'Require approval to activate,' add an approver, and enable 'Require justification on activation'
C) In Access reviews, create a recurring review for the Global Administrator role
D) In the Notifications tab, add the approver's email as a recipient for role activation alerts

---

**Q14.** Microsoft Entra ID Protection flags a user account through a leaked credentials detection, indicating the account's username and password were found exposed in a public breach dump. Which risk-based policy directly remediates this specific detection?

A) Configure a sign-in risk policy that requires MFA when sign-in risk is Medium or higher
B) Configure a Conditional Access policy requiring a compliant device for all users
C) Configure a named locations policy blocking sign-ins from countries outside the approved list
D) Configure a user risk policy that requires a secure password change when user risk is High

---

**Q15.** An administrator sets the SSPR policy so that 'Number of methods required to reset' is set to 2. A user has registered only one authentication method (mobile phone). What happens when this user attempts to reset their password using SSPR?

A) The user is automatically redirected to email-based verification as a fallback
B) The user cannot use SSPR until they register a second authentication method
C) The user can reset their password using the single registered method
D) The user's account is temporarily locked after the failed attempt

---

**Q16.** A company allows external partners (guest users) to access SharePoint Online for collaboration, but security wants to block those guests from downloading, printing, or syncing files when they connect from unmanaged devices, while still allowing normal browser-based access. Which Conditional Access session control should be applied?

A) Set Sign-in frequency to every 1 hour for guest users
B) Enable 'Persistent browser session' set to Always persistent
C) Add a Conditional Access grant control requiring the device to be Hybrid Azure AD joined
D) Enable 'Use Conditional Access App Control' with app-enforced restrictions in the session control

---

**Q17.** A company uses Microsoft Entra Privileged Identity Management (PIM) to manage the Global Administrator role. Security requires that eligible members must supply a business justification, complete Azure AD Multi-Factor Authentication, and receive approval from a designated approver every time they activate the role. Where should the administrator configure these requirements?

A) In a Conditional Access policy that targets the Global Administrator directory role
B) By making the role assignment permanent and scheduling a quarterly access review
C) In the PIM role settings for Global Administrator, on the Activation tab, by enabling justification, MFA, and approval requirements
D) In the Identity Protection sign-in risk policy for privileged accounts

---

**Q18.** A manufacturing company deploys shared kiosk workstations on the factory floor. Workers do not carry personal smartphones and need to sign in without typing a password. Which passwordless authentication method BEST fits this scenario?

A) Certificate-based authentication
B) Windows Hello for Business
C) FIDO2 security keys
D) Microsoft Authenticator passwordless sign-in

---

**Q19.** An organization has a highly sensitive finance application protected by Conditional Access. Security wants users to be re-prompted for authentication every 4 hours regardless of activity, even though 'Stay signed in' would normally keep them signed in longer. Which Conditional Access session control should be configured?

A) Sign-in frequency, set to 4 hours
B) Persistent browser session, set to Never persistent
C) Use app enforced restrictions
D) Cloud app security session control set to Monitor only

---

**Q20.** A company wants any user whose Microsoft Entra ID Protection user risk reaches 'High' to be forced to change their password before they can access any resource, while sign-in risk detections are handled separately with an MFA requirement. Which policy configuration achieves the password-change requirement?

A) A user risk policy with risk level High and grant control 'Require password change'
B) A Conditional Access sign-in risk policy with risk level High and grant control 'Require MFA'
C) Enable Security Defaults for the entire tenant
D) A Conditional Access policy that blocks all access when any risk is detected

---

**Q21.** An administrator enables Self-Service Password Reset (SSPR) for all users in the tenant and leaves the 'Number of methods required to reset' setting at its default value. What is the default minimum number of authentication methods a user must register to satisfy this requirement?

A) 1
B) 3
C) 4
D) 2

---

**Q22.** A company already enforces several Conditional Access policies (Microsoft Entra ID P1 licensed) and wants to add a new policy specifically to block all legacy authentication protocols, such as POP, IMAP, and older Office desktop clients, for all users except a break-glass account. Which approach should the administrator take?

A) Create a Conditional Access policy with the client apps condition set to legacy authentication clients, grant control set to Block access, and exclude the break-glass account
B) Create an Exchange Online mail flow rule that rejects legacy protocol connections
C) Enable Security Defaults for the tenant in addition to the existing Conditional Access policies
D) Configure the Authentication Methods policy to disable legacy authentication protocols

---

**Q23.** A company runs a GitHub Actions pipeline that must authenticate to Microsoft Entra ID to deploy resources to Azure. The security team requires that no client secrets or certificates be stored anywhere in the pipeline configuration. Which solution BEST meets this requirement?

A) Store a client secret in GitHub encrypted secrets and rotate it every 30 days
B) Configure a federated credential on the app registration that trusts OIDC tokens issued by GitHub Actions
C) Assign a system-assigned managed identity to the GitHub Actions runner
D) Upload an X.509 certificate to the app registration and store the private key in GitHub secrets

---

**Q24.** An organization has 20 Azure Virtual Machines across multiple resource groups that all need identical access to a Key Vault. The identity must be manageable independently of any single VM's lifecycle and reused across all 20 VMs. Which identity type should be configured?

A) A system-assigned managed identity on each of the 20 VMs
B) A user-assigned managed identity shared across all 20 VMs
C) A single app registration with a shared client secret distributed to all VMs
D) A group-assigned managed identity applied to the resource groups

---

**Q25.** A backend daemon service runs unattended with no signed-in user and needs to read directory data through Microsoft Graph. Which permission type must be configured on the app registration, and what additional step is required?

A) Delegated permissions; the app can request them without any further action
B) Delegated permissions; each user must consent individually the first time they sign in
C) Application permissions; consent is granted automatically as soon as the permissions are added
D) Application permissions; an administrator must grant admin consent

---

**Q26.** Which statement correctly describes the relationship between an app registration and a service principal in Microsoft Entra ID?

A) The service principal defines the application's global identity, while the app registration is the local representation used to consent to permissions in a specific tenant
B) An app registration and a service principal are two names referring to the exact same underlying object
C) The app registration defines the global identity of the application, while the service principal is the local instance in a tenant that is granted access to resources
D) A service principal exists only for managed identities, while human-facing applications use app registrations exclusively without a service principal

---

**Q27.** A security audit finds that several app registrations use client secrets that expire yearly, and expired secrets have caused multiple production outages. Which change would BEST reduce this operational risk for new integrations going forward?

A) Extend all client secret expiration periods to the maximum allowed value of 5 years
B) Where possible, replace client secrets with managed identities or workload identity federation
C) Replace client secrets with certificates only, since certificates never expire
D) Create a shared service account with a password that never expires and use it for all integrations

---

**Q28.** An organization wants to apply Conditional Access policies to service principals used by workload identities, blocking sign-ins from outside approved IP ranges. Which requirement must be met to enable this capability?

A) Legacy authentication protocols must be enabled for the workload identities
B) Workload identities automatically support Conditional Access with no additional licensing
C) The organization must have a Microsoft Entra Workload ID Premium license
D) Conditional Access can only be applied to user accounts, not to service principals

---

**Q29.** A company runs a CI/CD pipeline in GitHub Actions that deploys infrastructure to Azure. Security requires that no secrets or certificates be stored in GitHub for this integration. Which configuration on the Microsoft Entra app registration BEST meets this requirement?

A) Generate a client secret with a 24-month expiration and store it as a GitHub Actions encrypted secret
B) Assign a system-assigned managed identity to the GitHub-hosted runner and grant it the required Azure RBAC role
C) Upload a self-signed certificate's private key to the GitHub repository's encrypted secrets store
D) Configure a federated identity credential on the app registration that trusts OIDC tokens issued by GitHub Actions for the specific repository and environment

---

**Q30.** An Azure Function App runs a nightly job that must read directory data (user and group objects) from Microsoft Graph with no signed-in user involved. The solution must avoid managing any credentials manually. What should you configure?

A) Register an app with delegated User.Read permission and store the client secret in Azure Key Vault
B) Enable a system-assigned managed identity on the Function App and grant it the Directory.Read.All application permission with admin consent on Microsoft Graph
C) Create a service principal with a certificate credential and rotate the certificate manually every 12 months
D) Enable a system-assigned managed identity on the Function App and grant it the Directory.Read.All delegated permission

---

**Q31.** Your team is designing federated identity credentials for a single Microsoft Entra application registration that must authenticate workloads running in GitHub Actions, Kubernetes, and Terraform Cloud. What is the maximum number of federated identity credentials that can be configured on a single application object?

A) 20
B) 5
C) 50
D) Unlimited

---

**Q32.** Contoso publishes a multi-tenant SaaS application registered in the Contoso tenant. An administrator at Fabrikam consents to install and use this application for their organization. What is created in the Fabrikam tenant as a result of this consent?

A) A duplicate application object identical to the one in the Contoso tenant
B) A managed identity scoped to Fabrikam's Azure subscription
C) A copy of Contoso's app registration credentials (secrets and certificates)
D) A service principal that locally represents the Contoso application and holds Fabrikam-specific permission grants and role assignments

---

**Q33.** A company wants employees to request access to a bundle of resources (a group, a Teams team, and a SharePoint site) through a single self-service request, requiring approval from the resource owner in stage one and the requestor's manager in stage two. Which Microsoft Entra ID Governance capability BEST meets this requirement?

A) Create an access review with two reviewers assigned
B) Create a lifecycle workflow with an approval task
C) Create a terms of use policy requiring manager sign-off
D) Create an access package in an entitlement management catalog with a two-stage approval policy

---

**Q34.** An organization wants new hires to automatically be added to the correct groups and receive a welcome email on their employee hire date, without any manual administrator intervention. Which capability should they configure?

A) A lifecycle workflow using the 'Onboard employee' template with a scheduled trigger based on employeeHireDate
B) An access review with auto-apply enabled
C) An entitlement management access package requiring manual approval
D) A Conditional Access policy requiring terms of use acceptance

---

**Q35.** An access review for a group is configured with 'If reviewers don't respond' set to 'No change' and auto-apply results is enabled. A reviewer does not respond before the review ends. What happens to the user's group membership?

A) The user's access remains unchanged because the 'No change' fallback decision is applied automatically
B) The user's access is automatically removed
C) The review automatically self-extends by 7 days
D) An alert is sent to the Global Administrator but the membership stays pending until a manual action is taken

---

**Q36.** A security team wants engineers to have zero standing access to the Global Reader role, requiring users to activate the role only when needed, complete an MFA challenge, provide a business justification, and limit activations to a maximum of 8 hours. Which Microsoft Entra capability should they configure?

A) Microsoft Entra Privileged Identity Management (PIM) with an eligible assignment and role settings requiring MFA, justification, and a maximum activation duration
B) A Conditional Access policy requiring MFA whenever the Global Reader role is used
C) An access package with a time-limited assignment duration
D) An access review scheduled to run every 8 hours

---

**Q37.** Which statement correctly differentiates a Terms of Use policy from an Access Review in Microsoft Entra ID Governance?

A) Terms of use recertifies whether users still need existing resource access, while access reviews require users to accept a legal document before first sign-in
B) Both features perform the identical recertification function and can be used interchangeably
C) Terms of use requires users to accept a document (often for compliance) before accessing a protected resource, while access reviews periodically validate whether existing access should continue
D) Terms of use applies only to external guest users, while access reviews apply only to internal employees

---

**Q38.** Users at a company are requesting access to third-party multi-tenant applications requesting high-impact permissions such as 'read all mail'. The company wants to prevent users from self-consenting to such apps while still allowing admins to review requests and letting users self-consent to trusted, low-impact apps from verified publishers. Which Microsoft Entra capability should be configured?

A) A Conditional Access App Control policy
B) An access package that bundles the application as a catalog resource
C) User consent settings set to 'Do not allow user consent' combined with an admin consent workflow and an app consent policy permitting verified-publisher, low-impact app consent
D) A lifecycle workflow that removes app assignments for high-risk apps

---

**Q39.** A company records an employee's termination date in the on-premises HR system, which syncs to the employeeLeaveDateTime attribute in Microsoft Entra ID via Entra Connect. Security wants the employee's account automatically disabled and removed from all groups exactly 7 days after that attribute is populated, with no manual intervention. Which capability BEST meets this requirement?

A) A Lifecycle Workflow using the Leaver scenario, triggered on the employeeLeaveDateTime attribute with a 7-day execution offset
B) A recurring access review scoped to the affected security groups
C) An access package in entitlement management with a fixed expiration date
D) A Conditional Access policy that blocks sign-in for terminated users

---

**Q40.** Users at a company frequently request access to a line-of-business application that requires admin consent for its Microsoft Graph permissions. Currently, users hit a blocking error and must email IT manually. The company wants users to submit a request that specific reviewers can approve or deny directly in the Entra portal, without granting those users Global Administrator rights. Which capability should be configured to satisfy this requirement?

A) Change the tenant-wide user consent setting to 'Allow user consent for all apps'
B) Create an access package in entitlement management that grants the application role
C) Assign the affected users the Application Administrator role
D) Enable the admin consent workflow in Enterprise Applications > User consent settings, and assign a reviewer group

---

**Q41.** The security team wants quarterly access reviews on the Global Administrator role assigned through PIM for Microsoft Entra roles. If a reviewer takes no action, the decision must default to removing the eligible assignment, and approved removals must be applied automatically without further admin action. Which configuration achieves this?

A) In PIM > Microsoft Entra roles > Access reviews, create a recurring review with recurrence set to quarterly, 'If reviewers don't respond' set to Remove access, and Auto apply results to resource set to Enable
B) In PIM > Microsoft Entra roles > Access reviews, create a recurring review with 'If reviewers don't respond' set to No change, and Auto apply results set to Disable
C) Create an entitlement management access review on the catalog containing the Global Administrator role assignment
D) Configure a Conditional Access policy requiring reauthentication for users in the Global Administrator role every 90 days

---

**Q42.** Which Microsoft Entra ID Governance feature requires a user to explicitly view and accept a compliance or legal statement before being granted access to an application, and provides administrators with a report showing which users have and have not accepted it?

A) Entitlement management catalogs
B) Terms of use
C) Access reviews
D) Lifecycle workflows

---

