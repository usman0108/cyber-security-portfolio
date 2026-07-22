# SIEM Log Analysis Report

## 1. Executive Summary
A simulated SIEM-style log analysis investigation was completed using web server logs. The investigation identified suspicious activity including directory scanning, repeated failed login attempts, SQL injection-style requests, cross-site scripting attempts, and suspicious automated user-agent behaviour.

## 2. Scope
The analysis focused on simulated web server log events from 22 July 2026. The objective was to identify suspicious source IP addresses, review attack indicators, and recommend remediation actions.

## 3. Key Findings

| Finding | Source IP | Evidence | Severity |
|---|---|---|---|
| Directory scanning | 203.0.113.88 | Multiple requests to admin, config, backup and environment paths | Medium |
| Repeated failed login attempts | 203.0.113.88 | Five failed login attempts against admin account | High |
| SQL injection-style request | 192.0.2.55 | URL contained `' OR '1'='1` pattern | High |
| Cross-site scripting attempt | 192.0.2.55 | URL contained `<script>alert(1)</script>` | High |
| Suspicious user agent | 203.0.113.88 | Repeated use of `python-requests` | Medium |

## 4. Analysis
The activity from `203.0.113.88` suggests automated reconnaissance and possible brute-force activity. The source IP attempted to access common administrative and sensitive paths such as `/admin`, `/wp-admin`, `/config.php`, `/backup.zip`, and `/.env`. The same IP also generated repeated failed login attempts against the `admin` username.

The activity from `192.0.2.55` suggests web application attack attempts. The request containing `' OR '1'='1` is consistent with SQL injection testing. The request containing `<script>alert(1)</script>` is consistent with cross-site scripting testing.

## 5. Indicators of Compromise

| IoC Type | Value | Notes |
|---|---|---|
| IP Address | 203.0.113.88 | Repeated scanning and failed login activity |
| Defanged IP | 203[.]0[.]113[.]88 | Safe sharing format |
| IP Address | 192.0.2.55 | SQL injection and XSS-style requests |
| Defanged IP | 192[.]0[.]2[.]55 | Safe sharing format |
| URL Path | /wp-admin | Reconnaissance attempt |
| URL Path | /.env | Sensitive file discovery attempt |
| Pattern | `' OR '1'='1` | SQL injection-style payload |
| Pattern | `<script>alert(1)</script>` | XSS-style payload |

## 6. Risk
The main risks include:
- Unauthorised access through brute-force login attempts
- Discovery of sensitive files or exposed admin panels
- SQL injection against web application parameters
- Cross-site scripting against user input fields
- Increased attack surface from exposed paths or weak authentication controls

## 7. Recommended Remediation
- Block or investigate suspicious source IP addresses.
- Review authentication logs for successful logins from suspicious IPs.
- Enforce MFA for administrative accounts.
- Apply account lockout or rate limiting to login pages.
- Review and harden exposed web directories.
- Ensure sensitive files such as `.env` and backups are not publicly accessible.
- Use a web application firewall to help block SQL injection and XSS attempts.
- Validate and sanitise user input in web applications.
- Monitor for repeated 401, 403 and 404 events from the same source IP.
- Escalate to the security team if successful compromise is identified.

## 8. Lessons Learned
This project helped practise reviewing web server logs, identifying suspicious source IPs, recognising brute-force and web attack indicators, and documenting findings in a SOC-style report.

## 9. Conclusion
The simulated log analysis identified multiple suspicious behaviours that would require investigation in a real SOC environment. The findings demonstrate the importance of log monitoring, alert triage, web application security, and clear incident documentation.
