# 90 - AI Security Operations
## Overview
AI Security Operations covers monitoring, anomaly detection, incident response, and auditing for AI systems running in production.

## 1. Monitoring AI Systems in Production
| Metric | What It Detects |
|--------|----------------|
| Input distribution shift | Unusual query patterns, potential attacks |
| Output toxicity rate | Guardrail bypass attempts |
| Latency spikes | DoS attacks or resource exhaustion |
| Error/exception rate | Model failures, adversarial inputs |
| API auth failure rate | Unauthorized access attempts |
| Guardrail trigger rate | Volume of blocked requests |
| Token usage per user | Model extraction via high-volume queries |

### Monitoring Stack
- Application logs: all inputs, outputs, timestamps, user IDs
- ML monitoring: Evidently AI, WhyLabs, Arize for drift
- SIEM integration: forward AI logs to Splunk/Elastic
- Alerting: PagerDuty for critical safety events

## 2. AI Incident Types and Response
| Incident | Example | Response |
|----------|---------|----------|
| Jailbreak in production | Harmful output generated | Log, patch guardrail, user review |
| Prompt injection attack | External content hijacked agent | Isolate agent, audit all actions taken |
| Model extraction | 1M+ queries from single IP | Block IP, rotate API keys |
| Data leakage | Model outputs training PII | Take offline, investigate scope |
| Model poisoning | Fine-tuned model behaves abnormally | Roll back to previous version |

### AI IR Playbook Steps
1. Detect: alert fires (anomaly, guardrail bypass, rate limit exceeded)
2. Contain: disable endpoint or revert to safe model version
3. Investigate: review logs, reproduce attack, assess impact
4. Eradicate: patch guardrail, retrain if poisoned, fix root cause
5. Recover: redeploy with enhanced monitoring
6. Lessons Learned: update playbooks, guardrails, detection rules

## 3. Model Drift Detection
- **Data drift**: input distribution changes over time
- **Concept drift**: relationship between inputs and correct outputs changes
- **Model drift**: performance degrades in production

```python
# Using Evidently AI
from evidently.report import Report
from evidently.metric_preset import DataDriftPreset
import pandas as pd

report = Report(metrics=[DataDriftPreset()])
report.run(reference_data=training_df, current_data=production_df)
report.save_html("drift_report.html")
```

## 4. AI Audit Logging
Minimum fields to log per inference request:
```json
{
  "timestamp": "2024-01-15T14:32:11Z",
  "request_id": "req_abc123",
  "user_id": "user_456",
  "model": "claude-sonnet-4-6",
  "input_tokens": 150,
  "output_tokens": 300,
  "input_hash": "sha256:abc...",
  "guardrail_triggered": false,
  "guardrail_category": null,
  "latency_ms": 1240,
  "ip_address": "203.0.113.5"
}
```
