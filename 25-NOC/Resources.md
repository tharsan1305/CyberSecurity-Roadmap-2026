# Day 25 - Resources

## Tools Used
- Nagios Core / Zabbix (network monitoring)
- Ticketing system concepts (Jira Service Management, ServiceNow, Zendesk - reference only)

## Commands Reference
| Purpose | Command |
|---|---|
| Install Nagios (Debian/Ubuntu) | `sudo apt install nagios4 -y` |
| Run Zabbix via Docker | `docker run -d -p 80:80 zabbix/zabbix-appliance:latest` |
| Basic ping check | `ping <host>` |

## Key Terms Glossary
- **SLA**: Service Level Agreement, defines guaranteed performance/uptime commitments
- **Uptime**: percentage of time a system/service is operational
- **Latency**: delay in data transmission between source and destination
- **Packet Loss**: percentage of sent packets that never reach the destination
- **Tier 1/2/3 Support**: escalation levels from initial triage to senior/vendor-level troubleshooting

## Further Reading
- Nagios official documentation (nagios.org)
- Zabbix official documentation (zabbix.com/documentation)
- ITIL incident management framework overview (relevant to ticketing/escalation processes)

## Skills Gained Today
- Understanding NOC vs SOC roles
- Basic monitoring tool setup and threshold alerting
- Ticketing and escalation workflow concepts
