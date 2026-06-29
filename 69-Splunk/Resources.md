# Day 69 - Resources

## Tools Used
- Splunk Enterprise (free trial) or Splunk Cloud trial

## SPL Commands Reference
| Command | Purpose |
|---|---|
| `index=<name>` | Filter to a specific index |
| `sourcetype=<type>` | Filter by data type |
| `stats count by <field>` | Count events grouped by field |
| `eval new_field=expression` | Create/transform a field |
| `rex field=_raw "(?P<name>pattern)"` | Extract fields via regex |
| `table field1 field2` | Display specific fields |
| `sort -count` | Sort descending by count |

## Key Terms Glossary
- **SPL**: Search Processing Language
- **Index**: Splunk's storage partition for events
- **Universal Forwarder**: lightweight log shipper
- **HEC**: HTTP Event Collector

## Further Reading
- Splunk Fundamentals 1 (free course, splunk.com/training)
- Splunk Boss of the SOC (BOTS) - free CTF-style dataset for practice

## Skills Gained Today
- SPL query writing for security log analysis
- Splunk dashboard and alerting configuration
- Data ingestion method awareness
