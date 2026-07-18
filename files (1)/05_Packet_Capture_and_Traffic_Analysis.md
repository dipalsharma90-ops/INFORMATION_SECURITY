# Topic 5: Packet Capture and Traffic Analysis

### Goal
Capture live network traffic and analyze it to identify protocols, sessions, and suspicious activity.

### Core Tools
| Tool | Purpose |
|---|---|
| Wireshark | GUI packet analysis |
| `tcpdump` | CLI packet capture |
| `tshark` | CLI version of Wireshark |

### Setup Steps
1. List available capture interfaces:
```bash
tcpdump -D
```
2. Capture traffic on a specific interface (Ctrl+C to stop):
```bash
sudo tcpdump -i eth0 -w capture.pcap
```
3. Open the capture in Wireshark:
```bash
wireshark capture.pcap
```
4. Apply a filter to isolate HTTP traffic:
```
http
```
5. Follow a specific TCP stream: right-click a packet → **Follow > TCP Stream**.

### Verify Install
```bash
tcpdump --version
tshark --version
```

### Rules of Engagement
- Only capture traffic on networks/interfaces you own or are authorized to monitor — packet sniffing on others' traffic without consent is illegal in most jurisdictions.

### Checklist
- [ ] Captured a `.pcap` file successfully
- [ ] Opened and filtered it in Wireshark
- [ ] Followed a TCP stream to reconstruct a conversation
- [ ] Identified at least one protocol (HTTP/DNS/etc.) in the capture
