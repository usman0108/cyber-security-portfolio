# IoC Enrichment Notes

## Enrichment Summary

| IoC Type | Indicator | Enrichment Notes | Risk |
|---|---|---|---|
| IP Address | 203.0.113.77 | Observed as an outbound connection from the affected host shortly after suspicious PowerShell execution. | High |
| IP Address | 198.51.100.66 | Identified as an additional suspicious external IP for review. Requires log search across proxy, firewall and endpoint data. | Medium |
| Domain | update-checker.example | Suspicious domain contacted after malware-like activity. Domain name appears designed to look like a legitimate update service. | High |
| URL | hxxp://update-checker[.]example/download/update[.]exe | Suspicious download URL linked to unknown executable activity. | High |
| File Name | invoice_update.docm | Macro-enabled document linked to initial suspicious user activity. | High |
| File Path | C:\Users\a.brown\AppData\Roaming\update.exe | Executable created in user AppData path. This location is commonly abused by malware for persistence or payload execution. | High |
| SHA256 Hash | f2b3c4d5e6a79810b1c2d3e4f506172839405162738495a6b7c8d9e0f1a2b3c4 | Unknown file hash linked to suspicious endpoint behaviour. Should be searched across endpoint logs and blocked if confirmed malicious. | High |

## Defanged Indicators

| Original | Defanged |
|---|---|
| 203.0.113.77 | 203[.]0[.]113[.]77 |
| 198.51.100.66 | 198[.]51[.]100[.]66 |
| update-checker.example | update-checker[.]example |
| http://update-checker.example/download/update.exe | hxxp://update-checker[.]example/download/update[.]exe |

## Suggested Log Searches

### Search for suspicious IP connections
Search for outbound traffic to:
- 203.0.113.77
- 198.51.100.66

### Search for suspicious domain activity
Search DNS and proxy logs for:
- update-checker.example

### Search for suspicious file activity
Search endpoint logs for:
- invoice_update.docm
- update.exe
- C:\Users\a.brown\AppData\Roaming\update.exe

### Search for suspicious process activity
Search endpoint logs for:
- Microsoft Office spawning PowerShell
- powershell.exe making network connections
- PowerShell running unusual commands

## Notes
This enrichment is based on a simulated SOC investigation. The indicators are treated as suspicious due to their behaviour and context, not because they were checked against a live threat intelligence platform.
