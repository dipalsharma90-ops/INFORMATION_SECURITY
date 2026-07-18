# Topic 2: Linux System Administration Basics

### Goal
Get comfortable navigating, configuring, and troubleshooting Linux from the command line — the OS almost every security tool runs on.

### Core Tools
| Tool/Command | Purpose |
|---|---|
| `bash` | Default shell for scripting and navigation |
| `ls`, `cd`, `pwd` | File system navigation |
| `chmod`, `chown` | Permission and ownership management |
| `useradd`, `passwd` | User account management |
| `systemctl` | Service management |
| `apt` / `yum` / `dnf` | Package management |
| `grep`, `awk`, `sed` | Text processing |

### Setup Steps
1. Update package index and system:
```bash
sudo apt update && sudo apt full-upgrade -y
```
2. Create a non-root working user (avoid daily-driving as root):
```bash
sudo useradd -m -s /bin/bash student
sudo passwd student
sudo usermod -aG sudo student
```
3. Practice permission control on a test file:
```bash
touch test.sh
chmod 750 test.sh
chown student:student test.sh
```
4. Explore running services:
```bash
systemctl list-units --type=service --state=running
```
5. Write a simple automation script:
```bash
#!/bin/bash
echo "System check running..."
df -h
uptime
```

### Verify Install
```bash
whoami
id
systemctl status ssh
```

### Rules of Engagement
- Never run unfamiliar scripts as root without reading them first.
- Keep a backup/snapshot before editing system config files (e.g., `/etc/ssh/sshd_config`).

### Checklist
- [ ] Comfortable with file navigation (`ls`, `cd`, `pwd`, `find`)
- [ ] Created and tested a non-root user
- [ ] Practiced `chmod`/`chown`
- [ ] Wrote and ran a basic Bash script
- [ ] Explored `systemctl` service management
