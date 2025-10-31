# AWS — GuardDuty Repeated Findings
**Objective:** Group findings by instance to detect sustained activity.

```yaml
# Pseudo-Sigma scaffold; adapt to your source
title: GuardDuty Repeated Findings By Instance
status: test
logsource:
  product: aws
detection:
  selection:
    findingType: "*"
  condition: selection
level: medium
```
