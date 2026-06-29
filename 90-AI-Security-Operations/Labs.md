# 90 - AI Security Operations - Labs

## Lab 1: Model Extraction Detection
```python
from collections import defaultdict
from datetime import datetime

# Simulate API request log
requests = [
    {"user": "attacker", "ts": "10:00:01", "tokens": 500},
    {"user": "attacker", "ts": "10:00:02", "tokens": 500},
    {"user": "attacker", "ts": "10:00:03", "tokens": 500},
    {"user": "normal",   "ts": "10:05:00", "tokens": 200},
]
# Simulate 1000 requests from attacker in 1 minute
requests += [{"user":"attacker","ts":"10:00:59","tokens":500}]*996

counts = defaultdict(int)
for r in requests:
    counts[r["user"]] += 1

THRESHOLD = 100
for user, count in counts.items():
    if count > THRESHOLD:
        print(f"[ALERT] Possible model extraction: user={user}, requests={count}/min")
    else:
        print(f"[OK] user={user}, requests={count}")
```

## Lab 2: AI Incident Response Drill
**Scenario**: Production chatbot is generating harmful political content.

Work through all 6 IR steps:
1. **Detect**: What alert would fire? What logs would you check?
2. **Contain**: How do you take the model offline without full outage?
3. **Investigate**: How do you reproduce the harmful behavior?
4. **Eradicate**: Guardrail failure or training issue? How do you fix?
5. **Recover**: What tests do you run before redeploying?
6. **Report**: Write a 1-page AI incident report

## Lab 3: Build AI Audit Logging Middleware
```python
import hashlib, json
from datetime import datetime

def log_inference(user_id, model, prompt, response, latency_ms, guardrail_hit=False):
    log_entry = {
        "timestamp": datetime.utcnow().isoformat() + "Z",
        "user_id": user_id,
        "model": model,
        "input_hash": hashlib.sha256(prompt.encode()).hexdigest()[:16],
        "input_tokens": len(prompt.split()),
        "output_tokens": len(response.split()),
        "guardrail_triggered": guardrail_hit,
        "latency_ms": latency_ms,
    }
    print(json.dumps(log_entry, indent=2))
    return log_entry

log_inference("user_123", "claude-sonnet-4-6", "What is SQL injection?",
              "SQL injection is...", 850)
```

## Practice Challenges
- [ ] Set up Evidently AI and detect drift between two CSV datasets
- [ ] Write a complete AI IR playbook for a jailbreak incident
- [ ] Build a Grafana dashboard plan for AI security metrics (sketch layout)
- [ ] Research how OpenAI and Anthropic handle safety incidents publicly
