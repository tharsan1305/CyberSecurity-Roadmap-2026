# Day 70 - Lab: Threat Detection

## Objective
Configure a basic detection rule in Wazuh and explore Suricata for network-level detection.

## Task 1: Write a Custom Wazuh Detection Rule
Create a custom rule in `/var/ossec/etc/rules/local_rules.xml` on your Wazuh Manager:
```xml
<group name="custom_detection">
  <rule id="100100" level="12">
    <if_group>syslog</if_group>
    <match>nc -e\|/bin/bash\|/bin/sh</match>
    <description>Possible reverse shell attempt detected</description>
  </rule>
</group>
```
Restart Wazuh Manager, then simulate a log event matching the pattern and verify the alert fires.

## Task 2: Install and Run Suricata
```bash
sudo apt install suricata -y
sudo suricata -c /etc/suricata/suricata.yaml -i eth0 --af-packet
sudo tail -f /var/log/suricata/fast.log
```

## Task 3: Test a Suricata Detection
```bash
curl http://testmynids.us/uid/index.html
```
Check if Suricata's default rules trigger an alert in fast.log.

## Results
| Item | Value |
|---|---|
| Custom Wazuh rule created (Y/N) | |
| Custom alert triggered (Y/N) | |
| Suricata installed (Y/N) | |
| Suricata alert generated (Y/N) | |

## Lab Summary
Note the difference between host-based (Wazuh/EDR) and network-based (Suricata) detection perspectives.
