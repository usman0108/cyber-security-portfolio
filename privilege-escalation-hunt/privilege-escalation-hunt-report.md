# Privilege Escalation Hunt Report

## 1. Executive Summary
A simulated privilege escalation investigation was completed after a standard user account was added to a privileged administrator group. The activity included failed login attempts, a successful remote login, privileged group membership changes, special privileges being assigned, and suspicious PowerShell execution.

The activity was assessed as suspicious because a non-administrative account received elevated privileges shortly after unusual authentication activity.

## 2. Key Details

| Field | Details |
|---|---|
| Affected account | temp.user |
| Source IP | 10.0.1.45 |
| Privileged group | Domain Admins |
| Local admin group | Administrators |
| Suspicious process | powershell.exe |
| Suspicious command | ExecutionPolicy Bypass |
| Severity | High |

## 3. Timeline

| Time | Event |
|---|---|
| 09:10:14 | Failed login for temp.user |
| 09:11:02 | Second failed login for temp.user |
| 09:12:31 | Successful remote login for temp.user |
| 09:14:08 | temp.user added to Domain Admins |
| 09:16:22 | Special privileges assigned to temp.user |
| 09:18:40 | PowerShell launched with ExecutionPolicy Bypass |
| 09:21:05 | temp.user added to local Administrators group |
| 09:26:33 | temp.user removed from Domain Admins |
| 09:30:12 | admin.jones logged in interactively |

## 4. Analysis
The activity suggests possible privilege escalation or misuse of administrative permissions. The account temp.user experienced failed login attempts before a successful remote login. Shortly after this, the account was added to the Domain Admins group, which provides a high level of access in a Windows domain environment.

The account then received special privileges and launched PowerShell using ExecutionPolicy Bypass. This is suspicious because attackers may use PowerShell to run scripts, bypass restrictions, or continue post-compromise activity.

The account was later removed from the Domain Admins group. This could be legitimate administrative activity, but it could also indicate an attempt to hide suspicious privilege changes.

## 5. Risk
The main risks include:
- Unauthorised privilege escalation
- Administrative account misuse
- Lateral movement
- Security control bypass
- Persistence through local administrator access
- Potential access to sensitive systems or data

## 6. Recommended Remediation
- Confirm whether the group membership change was authorised.
- Review the admin.jones account for possible compromise.
- Temporarily disable or restrict temp.user until verified.
- Remove unnecessary privileged access.
- Review PowerShell logs and command history.
- Check for similar privilege changes across the environment.
- Enforce least privilege access.
- Enable alerting for privileged group membership changes.
- Review MFA and conditional access controls for admin accounts.
- Escalate to the security team if compromise is confirmed.

## 7. Lessons Learned
This project helped practise identifying suspicious privilege escalation activity, reviewing Windows security events, analysing user and group changes, and documenting response actions in a SOC-style report.

## 8. Conclusion
The simulated investigation showed how privilege escalation can be detected through event log review and user activity analysis. Monitoring privileged group changes, special privilege assignments and suspicious PowerShell execution is important for identifying possible account compromise.
