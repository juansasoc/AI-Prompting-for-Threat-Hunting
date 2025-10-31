# Elastic / ESQL — Index Injection Patterns
**Objective:** Detect query injection or suspicious wildcards.

```esql
FROM elasticsearch.audit
| WHERE query LIKE "%*%" OR query LIKE "%(?i)(drop|delete|shutdown)%"
| STATS count() BY user.id, source.ip
```
