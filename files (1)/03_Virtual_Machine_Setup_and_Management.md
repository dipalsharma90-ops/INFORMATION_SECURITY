# Topic 3: Virtual Machine Setup and Management

### Goal
Build a repeatable, disposable lab of attacker + victim VMs on an isolated virtual network.

### Core Tools
| Tool | Purpose |
|---|---|
| VirtualBox / VMware Workstation | Hypervisor |
| Metasploitable 2/3 | Intentionally vulnerable victim VM |
| DVWA (Damn Vulnerable Web App) | Vulnerable web app for practice |
| VBoxManage | CLI control of VirtualBox |

### Setup Steps
1. Create an isolated internal network so VMs can talk to each other but not your real LAN:
```bash
VBoxManage natnetwork add --netname LabNet --network "10.0.5.0/24" --enable
```
2. Attach both attacker (Kali) and victim (Metasploitable) VMs to `LabNet`.
3. Boot the victim VM and note its IP:
```bash
ip addr show
```
4. From Kali, confirm connectivity:
```bash
ping -c 3 10.0.5.15
```
5. Snapshot both VMs once configured:
```bash
VBoxManage snapshot "Metasploitable" take "clean-baseline"
```

### Verify Install
```bash
VBoxManage list vms
VBoxManage list natnetworks
```

### Rules of Engagement
- Victim VMs are deliberately insecure — never expose them to the internet or a shared network.
- Always revert to snapshot after a destructive test (e.g., after a successful exploit that corrupts the VM).

### Checklist
- [ ] Isolated lab network created
- [ ] Attacker VM and victim VM can ping each other
- [ ] Both VMs snapshotted at a clean baseline
- [ ] Confirmed neither VM is bridged to the real network
