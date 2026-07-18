# Topic 12: System Log Monitoring and Analysis

### Goal
Collect, search, and interpret system/application logs to detect anomalies.

### Core Tools
| Tool | Purpose |
|---|---|
| `journalctl` | systemd log viewer |
| ELK Stack (Elasticsearch, Logstash, Kibana) | Centralized log analysis |
| Wazuh | Open-source SIEM/HIDS |
| `grep` / `awk` | Manual log searching |

### Setup Steps
1. View recent system logs:
```bash
journalctl -xe
```
2. Search authentication logs for failed logins:
```bash
sudo grep "Failed password" /var/log/auth.log
```
3. Run a basic Wazuh manager (Docker quick-start):
```bash
docker run -d --name wazuh-manager -p 1514:1514 -p 1515:1515 -p 55000:55000 wazuh/wazuh-manager
```
4. Tail a log file live while generating test activity:
```bash
tail -f /var/log/auth.log
```
5. Set up a simple alert rule (example: count failed SSH logins in the last hour):
```bash
grep "Failed password" /var/log/auth.log | grep "$(date '+%b %e %H')" | wc -l
```

### Verify Install
```bash
journalctl --version
docker ps
```

### Rules of Engagement
- Log files may contain sensitive data (usernames, IPs) — handle and store them securely, and only within your authorized lab.

### Checklist
- [ ] Viewed and filtered system logs
- [ ] Identified failed login attempts in auth logs
- [ ] Set up a basic centralized logging tool
- [ ] Created one simple detection/alert query
