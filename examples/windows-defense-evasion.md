# Windows — Defense Evasion (Disable Security Tools)
**Objective:** Detect attempts to disable Defender or auditing.

```kql
DeviceProcessEvents
| where FileName in ("powershell.exe","cmd.exe")
| where CommandLine has_any ("Set-MpPreference","DisableRealtimeMonitoring","wevtutil cl","sc stop windefend")
| project Timestamp, DeviceName, AccountName, CommandLine
```
