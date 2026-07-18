# Topic 1: Introduction to Security Tools and Environment Setup

### Goal
Set up a safe, isolated lab environment and get familiar with the core toolset used throughout this repo.

### Core Tools
| Tool | Purpose |
|---|---|
| VirtualBox / VMware | Run isolated virtual machines |
| Kali Linux / Parrot OS | Pre-loaded security testing distro |
| Wireshark | Packet capture and analysis |
| Nmap | Network scanning |
| Metasploit Framework | Exploitation framework (lab use only) |
| Burp Suite | Web app testing proxy |
| John the Ripper / Hashcat | Password cracking (auditing your own hashes) |

### Setup Steps
1. Install a hypervisor (VirtualBox recommended for beginners):
```bash
sudo apt update && sudo apt install virtualbox virtualbox-ext-pack -y
```
2. Download Kali Linux VM image from the official site: https://www.kali.org/get-kali/
3. Import the VM (`.ova` file) into VirtualBox: `File > Import Appliance`.
4. Allocate at least 4GB RAM and 40GB disk.
5. Set the VM's network adapter to **NAT Network** or **Host-only** — never bridge a testing VM directly onto a network you don't own.
6. Snapshot the clean VM state before any testing:
```bash
VBoxManage snapshot "Kali" take "clean-install"
```

### Verify Install
```bash
nmap --version
wireshark --version
msfconsole -v
```

### Rules of Engagement (read before anything else)
- Only test systems you own or have explicit written authorization to test.
- Keep all lab VMs on an isolated/host-only network.
- Document everything you do — screenshots, commands, timestamps.

### Checklist
- [ ] Hypervisor installed
- [ ] Kali/Parrot VM imported and updated (`sudo apt update && sudo apt full-upgrade -y`)
- [ ] Clean snapshot taken
- [ ] Core tools verified
