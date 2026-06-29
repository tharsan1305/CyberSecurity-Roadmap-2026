# Day 68 - Resources

## Tools Used
- Wazuh Manager + Agent (Docker deployment)
- OpenSearch/Kibana dashboard

## Commands Reference
| Purpose | Command |
|---|---|
| Deploy Wazuh (Docker) | `docker-compose up -d` (from wazuh-docker/single-node) |
| Start agent | `systemctl start wazuh-agent` |
| Check agent status | `systemctl status wazuh-agent` |

## Key Terms Glossary
- **Manager**: central Wazuh server
- **Agent**: endpoint collector and forwarder
- **FIM**: File Integrity Monitoring
- **Rule Level**: Wazuh severity (1-15, 12+ = critical alerts)

## Further Reading
- Wazuh official documentation (documentation.wazuh.com)
- Wazuh GitHub (github.com/wazuh)

## Skills Gained Today
- Wazuh deployment and agent connection
- Rule-based detection triggering
- File Integrity Monitoring practical verification
- SIEM dashboard usage
