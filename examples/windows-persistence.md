# Windows — Suspicious PowerShell Downloads
**Objective:** Detect encoded commands and external downloads.

```kql
DeviceProcessEvents
| where FileName == "powershell.exe" and CommandLine contains "-enc"
| extend decoded = base64_decode_tostring(extract("-enc (.+)", 1, CommandLine))
| where decoded contains_any ("Invoke-WebRequest", "DownloadString", "Invoke-Expression")
| project Timestamp, AccountName, decoded
```
