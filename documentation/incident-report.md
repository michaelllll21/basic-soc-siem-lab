# Incident Report

## Incident Title
Multiple Failed Login Attempts and Account Lockout Detected

## Date and Time
July 2026

## Affected Device
Desktop1 / Windows 10 Domain Client

## Affected Account
SimoTech\Helpdesk

## Related Event IDs

| Event ID | Description |
|---|---|
| 4625 | Failed logon |
| 4624 | Successful logon |
| 4720 | User account created |
| 4740 | User account locked out |

---

## Incident Description

Multiple failed login attempts were generated and detected using Windows Event Viewer. The repeated failed logins resulted in the Helpdesk domain account being locked out. The account lockout was verified through the Windows login message and Event ID 4740 in the Security log.

This activity may represent a legitimate user entering the wrong password, unauthorized login attempts, or a possible brute-force attempt.

---

## Findings

- Failed login activity was detected using Event ID 4625.
- Successful login activity was verified using Event ID 4624.
- A new test user account was created and detected using Event ID 4720.
- The Helpdesk account became locked out after repeated failed login attempts.
- Account lockout activity was detected using Event ID 4740.
- The locked account was reviewed and unlocked through Active Directory Users and Computers.

---

## Impact

No confirmed compromise occurred in this lab environment. However, repeated failed login attempts and account lockouts can affect user productivity and may indicate suspicious authentication activity.

---

## Recommended Actions

- Verify whether the failed login attempts were made by the legitimate user.
- Review the source device and affected account.
- Check for repeated failed login attempts from unknown systems.
- Reset the password if suspicious activity is confirmed.
- Unlock the account only after confirming the user identity.
- Continue monitoring related successful and failed login events.
- Escalate repeated or suspicious login activity to a security administrator.

---

## Evidence

- Failed logon event: 4625
- Successful logon event: 4624
- User account created event: 4720
- Account lockout event: 4740
- Account unlock verification through Active Directory Users and Computers

---

## Status
Closed - Lab activity completed.
