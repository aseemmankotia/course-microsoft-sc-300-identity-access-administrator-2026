## Chapter 2: External Identities & Hybrid Identity Synchronization — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | Default password hash sync interval (after initial full sync)? | 2 minutes. Exam tip: separate from the 30-minute default delta sync cycle for other object attributes. |
| 2 | Minimum vs recommended number of PTA agents? | Minimum: 1. Recommended for HA: 3. Exam tip: agents make outbound-only connections on port 443 — no inbound firewall rules required. |
| 3 | What happens to sign-in if the AD FS farm goes down and PHS is not enabled as backup? | Users cannot authenticate at all — federation is a single point of failure. Exam tip: Microsoft recommends enabling PHS as a backup even when using federation. |
| 4 | What AD computer object does Seamless SSO create, and what does it hold? | AZUREADSSOACC — holds the Kerberos decryption key (AES256) used to issue silent sign-in tickets. Exam tip: works with PHS and PTA, not used with federation. |
| 5 | B2B collaboration vs B2B direct connect — which creates a guest object in the local directory? | B2B collaboration creates a guest object. B2B direct connect does NOT — users keep their home-tenant identity. Exam tip: direct connect is used for Teams shared channels. |
| 6 | Default inbound/outbound Cross-tenant access setting for B2B collaboration? | Allow, enabled by default for all external Entra tenants. Exam tip: B2B direct connect is blocked by default and must be explicitly enabled per organization. |
| 7 | Four options for 'who can invite guests' in External collaboration settings? | Everyone (including guests), Member users and users assigned to specific admin roles, Only users assigned specific admin roles, No one. Exam tip: default is the most permissive option. |
| 8 | What does Microsoft Entra Connect staging mode do? | Runs a parallel sync server with identical config that imports/syncs but does NOT export to AD or Entra ID, until promoted. Exam tip: used for safe server migration/DR testing. |
| 9 | Default Microsoft Entra Connect delta sync cycle interval? | 30 minutes. Exam tip: this is distinct from the 2-minute password hash sync interval. |
| 10 | Which sync tool: lightweight agents, easy multi-forest support, but only supports PHS (no PTA/Federation)? | Microsoft Entra Cloud Sync. Exam tip: choose full Entra Connect when PTA, Federation, or complex sync rules are required. |
| 11 | Three guest user access restriction levels in External collaboration settings? | Same as member users (default), Limited access, Most restrictive access. Exam tip: 'Same as member' lets guests enumerate directory objects broadly. |
| 12 | Do Pass-through Authentication agents store user passwords or hashes? | No — credentials are validated in real time against on-prem AD via an encrypted channel; nothing is stored in the agent or cloud. Exam tip: this is the key differentiator PTA has over PHS for compliance-sensitive orgs. |
