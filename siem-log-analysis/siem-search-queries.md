# SIEM Search Queries

## 1. Identify repeated failed login attempts

```spl
status=401 url="/login.php"
| stats count by src_ip, username
| where count >= 5
```

## 2. Identify suspicious scanning activity

```spl
status=404
| stats count by src_ip
| where count >= 5
```

## 3. Identify SQL injection-style requests

```spl
url="*OR*1*=*1*" OR url="*' OR '*'='*"
```

## 4. Identify cross-site scripting attempts

```spl
url="*<script>*" OR url="*alert(*)*"
```

## 5. Identify suspicious user agents

```spl
user_agent="python-requests"
| stats count by src_ip, user_agent
```

## Notes
These are beginner-friendly SIEM-style searches written to demonstrate how a SOC analyst might investigate suspicious web server activity.
