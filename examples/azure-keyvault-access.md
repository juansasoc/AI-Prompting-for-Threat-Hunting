# Azure — Key Vault Access Anomalies
**Objective:** Detect unusual IPs accessing secrets.

```kql
AzureDiagnostics
| where Category == "AuditEvent" and ResourceProvider == "MICROSOFT.KEYVAULT"
| summarize count() by CallerIPAddress, OperationName, ResultType
| order by count_ desc
```
