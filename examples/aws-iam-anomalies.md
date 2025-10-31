# AWS — IAM Anomalies
**Objective:** Detect unusual IAM actions from suspicious IPs.

```esql
FROM cloudtrail
| WHERE eventName IN ("CreateAccessKey","AttachUserPolicy")
| WHERE sourceIPAddress IN (TOR_IP_FEED)
| STATS count() BY userIdentity.userName, eventName, sourceIPAddress
```
