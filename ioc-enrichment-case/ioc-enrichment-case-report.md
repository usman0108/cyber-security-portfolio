# IoC Enrichment Case Report

## 1. Executive Summary
A simulated Indicator of Compromise enrichment investigation was completed after suspicious endpoint activity was identified on host WS-014. The incident involved a suspicious document attachment, PowerShell activity, outbound connections, suspicious domain activity, and creation of an unknown executable in the user's AppData directory.

The enriched indicators suggest possible phishing-led malware activity with potential command-and-control communication.

## 2. Case Details

| Field | Details |
|---|---|
| Case ID | IOC-2026-07-22-001 |
| Incident type | Suspected phishing-led malware activity |
| Affected host | WS-014 |
| Affected user | a.brown |
| Suspicious file | invoice_update.docm |
| Suspicious executable | update.exe |
| Suspicious domain | update-checker.example |
| Severity | High |

## 3. Indicators Reviewed

| IoC Type | Value | Defanged Value | Risk |
|---|---|---|---|
| IP Address | 203.0.113.77 | 203[.]0[.]113[.]77 | High |
| IP Address | 198.51.100.66 | 198[.]51[.]100[.]66 | Medium |
| Domain | update-checker.example | update-checker[.]example | High |
| URL | http://update-checker.example/download/update.exe | hxxp://update-checker[.]example/download/update[.]exe | High |
| File Name | invoice_update.docm | invoice_update[.]docm | High |
| File Path | C:\Users\a.brown\AppData\Roaming\update.exe | C:\Users\a.brown\AppData\Roaming\update[.]exe | High |
| SHA256 Hash | f2b3c4d5e6a79810b1c2d3e4f506172839405162738495a6b7c8d9e0f1a2b3c4 | N/A | High |

## 4. Analysis
The suspicious activity appears to have started with a macro-enabled document named invoice_update.docm. After the document was opened, Microsoft Office spawned PowerShell, which then attempted outbound communication to an external IP address.

The domain update-checker.example appears suspicious because it was contacted after script execution and resembles a fake update service. The URL linked to the domain also appears to serve an executable named update.exe.

The file path C:\Users\a.brown\AppData\Roaming\update.exe is suspicious because malware often uses user profile directories such as AppData to store payloads or maintain persistence.

The combination of a suspicious document, PowerShell execution, outbound network communication, suspicious domain activity and unknown executable creation suggests potential malware activity.

## 5. Risk Assessment
The case was rated as High severity because:
- A user opened a suspicious document attachment.
- PowerShell was spawned by Microsoft Office.
- The host attempted outbound communication to suspicious infrastructure.
- An unknown executable was created in the AppData directory.
- Multiple IoCs were linked to the same affected endpoint.
- The activity may indicate command-and-control communication.

## 6. Recommended Response Actions
- Isolate the affected host from the network.
- Block the suspicious IP addresses and domain.
- Search for the IoCs across firewall, DNS, proxy and endpoint logs.
- Check whether other hosts contacted the same indicators.
- Quarantine or remove the suspicious executable.
- Reset the affected user's password.
- Revoke active sessions if account compromise is suspected.
- Review email logs for similar attachments sent to other users.
- Submit the file hash for further analysis in a safe environment.
- Add detection rules for the suspicious file path, domain and PowerShell behaviour.
- Monitor for repeat activity after containment.

## 7. Lessons Learned
This project helped practise the process of reviewing raw indicators, defanging IoCs, adding investigation context, assessing risk and documenting response actions in a clear SOC-style report.

## 8. Conclusion
The simulated investigation demonstrated how IoC enrichment can support SOC analysis by connecting endpoint, network, domain and file-based evidence. Enriching indicators helps analysts understand risk, prioritise response actions and search for related activity across the wider environment.
