# Day 69 - Splunk

## Goal
Learn Splunk SPL (Search Processing Language) - the most widely used commercial SIEM in enterprise SOCs.

## 1. SPL (Search Processing Language)
Splunk's query language for searching, filtering, and transforming log data.

```splunk
index=main sourcetype=syslog "Failed password"
| stats count by src_ip
| sort -count
| head 10
```

Key commands:
- `search` / `index=` : filter events
- `stats count by <field>` : aggregate
- `eval` : create new fields
- `rex` : extract fields with regex
- `table` : display selected fields
- `sort` : order results
- `where` : filter after stats

## 2. Dashboards & Visualizations
SPL results can be saved as dashboard panels (charts, tables, maps). Common SOC dashboards show: failed login trends, top source IPs, alert volume over time.

## 3. Data Ingestion (Forwarders)
- **Universal Forwarder**: lightweight agent installed on endpoints, forwards logs to Splunk indexer
- **Heavy Forwarder**: parses/filters data before forwarding
- **HEC (HTTP Event Collector)**: REST API-based ingestion for custom apps/scripts

## 4. Alerting & Reports
Saved searches run on a schedule and trigger actions (email, webhook, ticket creation) when conditions are met.
```splunk
index=main "Failed password" | stats count by src_ip | where count > 10
```
Saved as alert: "Notify when any IP has >10 failed logins in 5 minutes."

## Interview Questions
**Q1. What does `stats count by src_ip` do in Splunk SPL?**
Groups events by source IP and counts the number of events per IP.
**Q2. How does a Universal Forwarder differ from a Heavy Forwarder?**
Universal Forwarder is lightweight and just forwards raw data; Heavy Forwarder parses and can filter/transform data before forwarding.
**Q3. What is an HEC in Splunk?**
HTTP Event Collector - a REST API endpoint for ingesting events directly from applications or scripts.

## Key Takeaways
- Learned SPL syntax for filtering, aggregation, and field extraction
- Learned dashboard creation from saved searches
- Learned data ingestion via forwarders and HEC
- Learned alerting/scheduled search configuration
