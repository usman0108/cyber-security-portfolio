# Insider Threat Use Case Report

## 1. Executive Summary
A simulated insider threat investigation was completed after unusual user activity was detected on a corporate laptop. The user accessed and downloaded multiple confidential files outside normal working hours, connected removable storage, copied files to external media, and sent a company file to a personal email address.

The activity was assessed as suspicious because it involved sensitive data access, after-hours activity, removable storage use, and possible data exfiltration indicators.

## 2. Key Details

| Field | Details |
|---|---|
| User | m.taylor |
| Department | Finance |
| Employment status | Notice period |
| Device | CORP-LAP-044 |
| Sensitive files accessed | Client contracts, payroll archive, finance backup |
| Removable storage used | Yes |
| Personal email used | Yes |
| Severity | High |

## 3. Timeline

| Time | Event |
|---|---|
| 08:55:12 | User logged in successfully |
| 09:10:33 | Confidential finance report opened |
| 10:22:41 | Confidential payroll file opened |
| 11:04:18 | Handover email sent internally |
| 18:47:55 | User logged in after normal working hours |
| 18:52:10 | Confidential client contracts downloaded |
| 18:54:22 | Confidential payroll archive downloaded |
| 18:57:49 | Supplier list downloaded |
| 19:02:15 | Confidential finance backup downloaded |
| 19:06:44 | Removable storage device connected |
| 19:08:20 | Client contracts copied to removable storage |
| 19:09:03 | Payroll archive copied to removable storage |
| 19:11:40 | Supplier list sent to personal email |
| 19:18:06 | User logged out |

## 4. Analysis
The activity suggests possible insider threat behaviour or attempted data exfiltration. The user was in the Finance department and was on their notice period, which can increase the need for careful access monitoring.

The user accessed and downloaded multiple confidential files after normal working hours. This included client contracts, payroll data and finance backup files. The user then connected removable storage and copied confidential files to it.

The user also sent a company file to a personal email address. While there may be legitimate explanations, the combination of after-hours access, bulk downloads, removable storage activity and personal email transfer is suspicious and should be investigated.

## 5. Indicators

| Indicator | Details |
|---|---|
| After-hours login | User logged in at 18:47:55 |
| Bulk downloads | Multiple files downloaded within a short time |
| Confidential data access | Payroll, client contracts and finance backup accessed |
| Removable storage | USB device connected |
| File copy activity | Confidential files copied to removable storage |
| Personal email | Company file sent to personal email |
| User risk factor | User was on notice period |

## 6. Risk
The main risks include:
- Data exfiltration
- Exposure of confidential company information
- Loss of client or payroll data
- Breach of company policy
- Insider misuse of authorised access
- Reputational and compliance impact

## 7. Recommended Remediation
- Escalate the activity to the security or management team.
- Confirm whether the file downloads and transfers were authorised.
- Disable or restrict removable storage if not required.
- Review the user's access permissions.
- Apply least privilege access controls.
- Search for similar activity across other users.
- Review email logs for external or personal email transfers.
- Preserve logs and evidence for investigation.
- Consider temporarily restricting the user account during review.
- Implement DLP controls for sensitive files.
- Create alerts for after-hours downloads of confidential data.

## 8. Lessons Learned
This project helped practise analysing user behaviour, identifying insider threat indicators, reviewing access logs, and documenting suspicious activity in a structured SOC-style report.

## 9. Conclusion
The simulated investigation demonstrated how insider threat behaviour may appear in user activity logs. Monitoring unusual access patterns, sensitive file downloads, removable storage use and personal email transfers can help detect potential data exfiltration early.
