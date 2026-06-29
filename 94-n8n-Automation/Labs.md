# 94 - n8n Automation - Labs

## Lab 1: First Workflow
1. Start n8n with Docker: `docker run -it --rm --name n8n -p 5678:5678 n8nio/n8n`
2. Open http://localhost:5678
3. Build: Schedule Trigger (every minute) -> HTTP Request (GET https://httpbin.org/ip) -> Slack (post IP)
4. Activate and verify

## Lab 2: IP Reputation Webhook
```
POST /webhook/check-ip {"ip": "185.220.101.5"}
  -> HTTP GET https://www.virustotal.com/api/v3/ip_addresses/{{ip}}
     Header: x-apikey = YOUR_KEY
  -> IF malicious > 0: Slack "ALERT: {{ip}} is malicious"
  -> ELSE: Slack "{{ip}} is clean"
```
Test: `curl -X POST WEBHOOK_URL -d '{"ip":"8.8.8.8"}'`

## Lab 3: Full SOC Automation
Build end-to-end: SIEM alert -> Claude API triage -> TheHive ticket -> Slack notification with severity and MITRE technique.

## Practice Challenges
- [ ] Daily CVE digest: NVD RSS feed filtered by CVSS > 8 -> Slack
- [ ] Phishing URL checker with automatic proxy block
- [ ] IOC enrichment pipeline: MISP feed -> AbuseIPDB -> blocklist
- [ ] AI triage workflow using Claude API
