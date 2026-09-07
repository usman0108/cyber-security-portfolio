# Detection Logic

## 1. Detect after-hours access to confidential files

Search logic:
classification="Confidential" AND time outside normal working hours

Purpose:
Identify users accessing sensitive files outside expected working hours.

## 2. Detect multiple confidential file downloads

Search logic:
action="downloaded" AND classification="Confidential"

Aggregation:
Count downloads by user within a short time period.

Alert condition:
More than 3 confidential files downloaded within 30 minutes.

Purpose:
Identify potential data collection or exfiltration preparation.

## 3. Detect removable storage activity

Search logic:
event="USB_DEVICE_CONNECTED" OR destination="removable_storage"

Purpose:
Identify possible copying of sensitive files to USB or external storage.

## 4. Detect email sent to personal account

Search logic:
EMAIL_SENT AND recipient contains personal email domain

Purpose:
Identify possible unauthorised transfer of company data to a personal account.

## 5. Detection Summary
The key detection idea is to look for a chain of suspicious events:
- User is on notice period
- After-hours login
- Access to confidential files
- Multiple sensitive file downloads
- USB storage connected
- Files copied to removable storage
- Email sent to personal account

## Notes
This detection logic is based on a simulated insider threat scenario and is written for beginner SOC-style analysis.
