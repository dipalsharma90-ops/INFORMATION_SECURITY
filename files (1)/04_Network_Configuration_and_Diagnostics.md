# Topic 4: Network Configuration and Diagnostics

### Goal
Understand and troubleshoot IP networking — addressing, routing, and DNS — using standard CLI tools.

### Core Tools
| Tool | Purpose |
|---|---|
| `ip` / `ifconfig` | View/configure interfaces |
| `ping` | Reachability test |
| `traceroute` / `tracert` | Path tracing |
| `netstat` / `ss` | Active connections/ports |
| `dig` / `nslookup` | DNS lookups |

### Setup Steps
1. Check current network configuration:
```bash
ip addr show
ip route show
```
2. Test reachability to a target:
```bash
ping -c 4 8.8.8.8
```
3. Trace the path packets take:
```bash
traceroute google.com
```
4. Inspect open ports/connections on your own machine:
```bash
ss -tulnp
```
5. Query DNS records:
```bash
dig google.com A
nslookup google.com
```

### Verify Install
```bash
ip -V
traceroute --version
dig -v
```

### Rules of Engagement
- Diagnostic scans (ping, traceroute) on systems you don't own should still stay within acceptable-use policies of your network/ISP.

### Checklist
- [ ] Identified your machine's IP, subnet, and gateway
- [ ] Successfully pinged an external host
- [ ] Traced a route to a public site
- [ ] Listed open ports with `ss`
- [ ] Performed a DNS lookup
