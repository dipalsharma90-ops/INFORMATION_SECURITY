# Topic 11: Firewall Configuration and Access Control

### Goal
Configure host-based firewall rules and apply access-control principles (least privilege, default-deny).

### Core Tools
| Tool | Purpose |
|---|---|
| `iptables` / `nftables` | Linux firewall rule management |
| `ufw` | Simplified firewall frontend |
| pfSense | Full firewall/router appliance (VM) |

### Setup Steps
1. Enable a simple default-deny firewall with UFW:
```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow ssh
sudo ufw enable
```
2. View active rules:
```bash
sudo ufw status verbose
```
3. Add a rule allowing a specific service (e.g., HTTP) only from your lab subnet:
```bash
sudo ufw allow from 10.0.5.0/24 to any port 80
```
4. Inspect and manage rules directly with iptables:
```bash
sudo iptables -L -v -n
```
5. Practice RBAC by creating a restricted sudo user:
```bash
sudo visudo
# add: student ALL=(ALL) /usr/bin/systemctl restart nginx
```

### Verify Install
```bash
sudo ufw status
sudo iptables --version
```

### Rules of Engagement
- Test firewall changes on a lab VM, not a production/remote server — a wrong rule can lock you out of SSH access.

### Checklist
- [ ] Default-deny firewall policy applied
- [ ] Confirmed only intended ports are reachable (via Nmap scan from another VM)
- [ ] Practiced least-privilege sudo rule
- [ ] Understand DAC vs MAC vs RBAC conceptually
