## Chapter 5: Microsoft Entra ID Protection: Risk Detections & Risk Policies — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | User risk policy default remediation action? | Require password change (self-service, via SSPR) or block access. Exam tip: User risk = tied to the ACCOUNT, remediation invalidates the compromised credential. |
| 2 | Sign-in risk policy default remediation action? | Require MFA (or block access). Exam tip: Sign-in risk = tied to a SPECIFIC SESSION, remediation just proves it's really the user for that sign-in — it does NOT reset the password. |
| 3 | Is 'Leaked credentials' a user risk or sign-in risk detection? | User risk detection — found offline (dark web/paste sites), tied to the account, not a specific sign-in event. |
| 4 | Is 'Anonymous IP address' a user risk or sign-in risk detection? | Sign-in risk detection — evaluated in real time during a specific sign-in attempt (e.g., Tor exit node). |
| 5 | Is 'Atypical travel' (impossible travel) a user or sign-in risk detection? | Sign-in risk detection — flags sign-ins from geographically impossible locations within a short time window relative to the same session/account activity. |
| 6 | Three risk levels used by Identity Protection? | Low, Medium, High (plus a 'No risk detected' state). Exam tip: policies let you pick the minimum risk level that triggers enforcement. |
| 7 | Prerequisites for a user to self-remediate risk? | SSPR must be enabled for the tenant, and the user must be registered for MFA/combined registration. Without both, an admin must remediate manually. |
| 8 | License required for full Identity Protection risk policies and investigation? | Microsoft Entra ID P2. P1 only allows a limited real-time sign-in risk CONDITION inside Conditional Access — not full user risk or the full detection catalog. |
| 9 | Where is risk-based enforcement configured today vs. legacy Identity Protection? | Legacy standalone 'User risk policy' / 'Sign-in risk policy' screens in Identity Protection are being retired. Current best practice: configure User risk and Sign-in risk CONDITIONS inside a Conditional Access policy. |
| 10 | Admin action: 'Confirm user compromised' — immediate effect? | Sets the user's risk level to High immediately, triggering whatever remediation the User risk policy specifies (typically forced password change or block). |
| 11 | Admin action: 'Dismiss user risk' — effect? | Manually closes the risky user detection without requiring password change. Used when the admin confirms the activity was legitimate (false positive). |
| 12 | Common exam trap: User risk policy vs Sign-in risk policy | Exam distractor pairs 'password change' with sign-in risk or 'MFA' with user risk — WRONG. Memory trick: User risk = 'U'nlock with password; Sign-in risk = 'S'atisfy with MFA per session. |
