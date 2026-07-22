# SIEM Search Queries

## 1. Identify repeated failed login attempts
```spl
status=401 url="/login.php"
| stats count by src_ip, username
| where count >= 5
