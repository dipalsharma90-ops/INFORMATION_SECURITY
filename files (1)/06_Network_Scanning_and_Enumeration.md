# Topic 6: Network Scanning and Enumeration

### Goal
Discover live hosts, open ports, running services, and gather enough detail to map the attack surface.

### Core Tools
| Tool | Purpose |
|---|---|
| Nmap | Host/port/service discovery |
| Masscan | High-speed port scanning |
| enum4linux | SMB/Windows enumeration |
| Netcat | Banner grabbing, manual probing |

### Setup Steps
1. Discover live hosts on the lab subnet:
```bash
nmap -sn 10.0.5.0/24
```
2. Scan a specific host for open ports and service versions:
```bash
nmap -sV -sC 10.0.5.15
```
3. Run a stealthier SYN scan (requires root):
```bash
sudo nmap -sS 10.0.5.15
```
4. Enumerate SMB shares on a Windows/Samba target:
```bash
enum4linux -a 10.0.5.15
```
5. Grab a service banner manually:
```bash
nc -nv 10.0.5.15 80
```

### Verify Install
```bash
nmap --version
enum4linux --help
nc -h
```

### Rules of Engagement
- Only scan hosts inside your authorized lab network (`10.0.5.0/24` in this setup).
- Aggressive scans can trigger IDS/IPS alerts or crash fragile services — never run against production systems without written authorization.

### Checklist
- [ ] Ran a host discovery scan across the subnet
- [ ] Identified open ports and service versions on a target
- [ ] Enumerated at least one service in detail (SMB/HTTP/FTP)
- [ ] Recorded results for the next phase (vulnerability assessment)
