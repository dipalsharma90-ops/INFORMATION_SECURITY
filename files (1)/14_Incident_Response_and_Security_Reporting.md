# Topic 14: Incident Response and Security Reporting

### Goal
Practice the structured process of detecting, containing, and documenting a security incident.

### Core Tools
| Tool | Purpose |
|---|---|
| NIST SP 800-61 framework | IR process reference |
| TheHive | Incident response case management |
| Volatility | Memory forensics |
| Timeline/report template (Markdown/Word) | Documentation |

### Setup Steps
1. **Preparation**: Confirm logging, backups, and contact list are ready before an incident occurs (checked in earlier topics).
2. **Identification**: Simulate detecting an incident from Topic 12's log alert (e.g., repeated failed logins followed by a success).
3. **Containment**: Isolate the "affected" lab VM from the network:
```bash
VBoxManage controlvm "VictimVM" nic1 null
```
4. **Eradication**: Identify and remove the root cause (e.g., delete a malicious cron job or user account):
```bash
crontab -l
sudo userdel -r malicioususer
```
5. **Recovery**: Restore the VM from a known-clean snapshot and reconnect it to the network.
6. **Reporting**: Write up a timeline — what happened, when, impact, and remediation — using a simple report template.

### Verify Install
```bash
crontab -l
VBoxManage list runningvms
```

### Rules of Engagement
- Always follow containment before eradication — removing evidence too early can destroy useful forensic data.

### Checklist
- [ ] Simulated detection of an incident
- [ ] Practiced containment (network isolation)
- [ ] Identified and removed root cause
- [ ] Restored system from clean backup/snapshot
- [ ] Wrote an incident report with timeline and impact
