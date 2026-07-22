# Incident Response Report

## 1. Executive Summary
A simulated security incident was investigated after an endpoint detection alert identified suspicious script execution on workstation WS-014. The activity began after a user opened a suspicious email attachment. Further investigation identified unusual PowerShell activity, outbound communication to a suspicious external IP address, suspicious DNS requests, and the creation of an unknown executable in the user's AppData directory.

The incident was assessed as a suspected phishing-led malware infection with possible command-and-control activity.

## 2. Incident Details

| Field | Details |
|---|---|
| Incident type | Suspected malware infection |
| Affected host | WS-014 |
| Affected user | a.brown |
| Initial vector | Suspicious email attachment |
| Suspicious attachment | invoice_update.docm |
| Suspicious process | PowerShell spawned by Microsoft Office |
| Suspicious IP | 203.0.113.77 |
| Defanged IP | 203[.]0[.]113[.]77 |
| Suspicious domain | update-checker.example |
| Defanged domain | update-checker[.]example |
| Severity | High |

## 3. Timeline

| Time | Event |
|---|---|
| 09:02:11 | User received suspicious email with attachment |
| 09:04:27 | User opened attachment |
| 09:05:03 | Microsoft Office spawned PowerShell |
| 09:05:18 | PowerShell attempted outbound connection |
| 09:06:44 | Endpoint detection alert triggered |
| 09:07:10 | Unusual outbound traffic detected |
| 09:09:35 | Unknown executable created in AppData |
| 09:12:02 | Suspicious DNS requests observed |
| 09:15:22 | SOC investigation began |
| 09:18:40 | Host isolated from network |
| 09:25:10 | User password reset requested |
| 09:40:33 | Malware scan initiated |
| 10:15:54 | Suspicious file removed |
| 10:32:18 | Endpoint patched and rebooted |
| 11:00:00 | Device monitored for further activity |

## 4. Analysis
The incident appears to have started with a suspicious email attachment. The attachment was opened by the user, after which Microsoft Office spawned a PowerShell process. This behaviour is suspicious because attackers often use malicious Office documents and scripts to execute commands on a victim machine.

The affected workstation then attempted outbound communication to a suspicious external IP address. An unknown executable was also created in the user's AppData directory, which may indicate malware persistence or payload delivery.

The combination of suspicious attachment execution, PowerShell activity, outbound network connections, and endpoint alerts suggests a likely malware infection caused by phishing.

## 5. Indicators of Compromise

| IoC Type | Value | Notes |
|---|---|---|
| Hostname | WS-014 | Affected endpoint |
| User | a.brown | Affected user account |
| File name | invoice_update.docm | Suspicious email attachment |
| Process | powershell.exe | Spawned by Microsoft Office |
| File path | C:\Users\a.brown\AppData\Roaming\update.exe | Suspicious executable |
| IP address | 203.0.113.77 | Suspicious outbound connection |
| Defanged IP | 203[.]0[.]113[.]77 | Safe sharing format |
| Domain | update-checker.example | Suspicious DNS activity |
| Defanged domain | update-checker[.]example | Safe sharing format |

## 6. Impact
The potential impact includes:
- Malware infection on the affected workstation
- Possible command-and-control communication
- Credential compromise
- Data exposure
- Further malware deployment
- Lateral movement inside the network

## 7. Incident Response Actions

### Detection
The incident was detected through an endpoint security alert showing suspicious script execution.

### Analysis
Logs and timeline evidence were reviewed to understand the affected host, user, suspicious process activity, outbound connections, and possible malware behaviour.

### Containment
The affected workstation was isolated from the network to prevent further communication with suspicious external infrastructure and reduce the chance of lateral movement.

### Eradication
The suspicious executable was removed, malware scanning was performed, and the affected system was patched.

### Recovery
The workstation was rebooted, monitored for further suspicious activity, and the user's password was reset.

### Lessons Learned
The incident highlighted the importance of phishing awareness, endpoint monitoring, PowerShell logging, MFA enforcement, email filtering, and rapid isolation of compromised devices.

## 8. Recommended Remediation
- Isolate affected endpoints quickly when malware activity is suspected.
- Reset passwords for affected users.
- Revoke active sessions where applicable.
- Block suspicious IPs and domains.
- Review email gateway logs for similar messages.
- Search for the same IoCs across other endpoints.
- Enable or review PowerShell logging.
- Ensure endpoint protection is active and updated.
- Enforce MFA for user accounts.
- Provide phishing awareness training to users.
- Review attachment filtering policies.
- Patch affected systems before returning them to normal use.

## 9. Conclusion
The simulated investigation demonstrated how a SOC analyst could respond to a suspected phishing-led malware incident. The report followed the incident response lifecycle and documented key evidence, indicators of compromise, impact, response actions, and remediation recommendations.
