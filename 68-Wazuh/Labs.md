# Day 68 - Lab: Wazuh

## Objective
Deploy Wazuh and trigger real alerts from your lab environment.

## Task 1: Deploy Wazuh via Docker
```bash
git clone https://github.com/wazuh/wazuh-docker
cd wazuh-docker/single-node
docker-compose up -d
```
Access the Wazuh dashboard at https://localhost (default credentials: admin/SecretPassword).

## Task 2: Connect a Wazuh Agent
On your Kali or Ubuntu VM:
```bash
curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | sudo apt-key add -
echo "deb https://packages.wazuh.com/4.x/apt/ stable main" | sudo tee /etc/apt/sources.list.d/wazuh.list
sudo apt update
sudo apt install wazuh-agent -y
sudo WAZUH_MANAGER='<manager-ip>' systemctl start wazuh-agent
```

## Task 3: Trigger a Brute Force Alert
Run multiple failed SSH attempts against the monitored machine from another machine in your lab:
```bash
for i in {1..10}; do ssh wronguser@<monitored-vm-ip> 2>/dev/null; done
```
Check Wazuh dashboard for triggered alerts.

## Task 4: Check FIM Alerts
Modify a monitored file on the agent:
```bash
echo "test" >> /etc/hosts
```
Wait ~1 minute, check Wazuh dashboard for FIM alert.

## Results
| Item | Value |
|---|---|
| Wazuh deployed (Y/N) | |
| Agent connected (Y/N) | |
| Brute force alert triggered (Y/N) | |
| FIM alert triggered (Y/N) | |

## Lab Summary
Note how quickly Wazuh detected the brute force and FIM events versus manually parsing logs (Topic 67).
