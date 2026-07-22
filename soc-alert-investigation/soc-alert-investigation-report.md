# SOC Alert Investigation Report

## 1. Alert Summary
A suspicious authentication alert was investigated after multiple failed login attempts were detected against a user account, followed by a successful login from the same external IP address. The investigation also identified post-login activity including a password change and the creation of an external email forwarding rule.

## 2. Evidence Reviewed

| Evidence | Finding |
|---|---|
| Affected user | j.smith |
| Suspicious source IP | 203.0.113.45 |
| Defanged source IP | 203[.]0[.]113[.]45 |
| Location | Netherlands |
| Failed login attempts | 5 failed attempts |
| Successful login | Successful login occurred after failed attempts |
| MFA status | MFA was not used |
| Post-login activity | Password change and external email forwarding rule created |
| Later user activity | User later reported suspicious activity from the United Kingdom |

## 3. Timeline of Events

| Time | Event |
|---|---|
| 09:14:03 - 09:15:26 | Multiple failed login attempts against j.smith |
| 09:16:04 | Successful login from the same suspicious IP |
| 09:17:40 | Password change recorded |
| 09:19:12 | External email forwarding rule created |
| 09:25:55 | User logged in from the United Kingdom with MFA |
| 09:26:21 | User reported suspicious activity |

## 4. Analysis
The activity suggests a possible credential-based attack. Multiple failed login attempts were followed by a successful login from the same suspicious external IP address. This is concerning because MFA was not used during the successful login.

The password change and external email forwarding rule created shortly after the login may indicate account compromise. External forwarding rules are commonly used by attackers to maintain access to emails or exfiltrate sensitive information.

## 5. Likely Attack Type
The activity is consistent with a brute-force or credential-based attack that may have resulted in account compromise.

## 6. Risk
The main risks include:
- Unauthorised account access
- Credential compromise
- Data exposure through external email forwarding
- Persistence through mailbox rule abuse
- Further phishing or lateral movement using the compromised account

## 7. Recommended Remediation
- Temporarily lock or disable the affected account.
- Reset the user's password.
- Revoke active sessions and access tokens.
- Enable or enforce MFA for the account.
- Remove the suspicious external email forwarding rule.
- Review mailbox activity and authentication logs.
- Investigate or block the suspicious source IP.
- Check whether other accounts show similar login patterns.
- Escalate the incident if compromise is confirmed.

## 8. Lessons Learned
This project helped practise SOC alert triage, authentication log analysis, identification of suspicious login behaviour, recognition of post-compromise activity, and documentation of response actions in a clear investigation report.
