# Elastic / ESQL — Lateral Movement (WinRM)
**Objective:** Identify PowerShell/WinRM remote sessions.

```esql
FROM endpoint.process
| WHERE process.command_line LIKE "%winrm%" OR process.command_line LIKE "%Enter-PSSession%"
| STATS count() BY host.name, user.name, destination.ip
```
