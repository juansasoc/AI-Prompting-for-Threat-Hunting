# Azure — Risky Sign-ins (Impossible Travel)
**Objective:** Detect sign-ins from distant geos within a short window.

```kql
SigninLogs
| summarize loginCountries = make_set(Location), minTime=min(TimeGenerated), maxTime=max(TimeGenerated) by UserPrincipalName
| where array_length(loginCountries) > 1 and datetime_diff("hour", minTime, maxTime) < 1
| project UserPrincipalName, loginCountries, minTime, maxTime
```
