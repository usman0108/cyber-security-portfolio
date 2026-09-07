# Detection Logic

## 1. Detect users added to privileged groups

Search logic:
EventID=4728 OR EventID=4732

Filter:
Group="Domain Admins" OR Group="Administrators"

Purpose:
Identify accounts being added to privileged groups.

## 2. Detect special privileges assigned to a user

Search logic:
EventID=4672

Purpose:
Identify accounts receiving administrative-level privileges after login.

## 3. Detect suspicious PowerShell activity

Search logic:
EventID=4688 AND Process="powershell.exe"

Filter:
Command contains "ExecutionPolicy Bypass"

Purpose:
Identify potentially suspicious PowerShell execution.

## 4. Detect failed logins followed by successful login

Search logic:
EventID=4625 OR EventID=4624

Filter:
Account="temp.user"

Purpose:
Review authentication activity before and after the privilege change.

## 5. Detection Summary
The key detection idea is to look for a chain of suspicious events:
- Failed logins
- Successful remote login
- User added to privileged group
- Special privileges assigned
- Suspicious PowerShell command
- Local administrator group change

## Notes
This detection logic is written for a beginner SOC-style investigation and is based on simulated Windows security events.
