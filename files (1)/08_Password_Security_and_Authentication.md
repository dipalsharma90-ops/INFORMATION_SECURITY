# Topic 8: Password Security and Authentication

### Goal
Understand how passwords are attacked and defended, and practice auditing hash strength safely.

### Core Tools
| Tool | Purpose |
|---|---|
| John the Ripper | Offline password cracking |
| Hashcat | GPU-accelerated password cracking |
| Hydra | Online brute-force login testing |
| CrackStation wordlists / rockyou.txt | Common wordlists |

### Setup Steps
1. Install cracking tools:
```bash
sudo apt install john hashcat hydra -y
```
2. Generate a sample hash to practice on (your own test password, not a real account):
```bash
echo -n "TestPass123" | sha256sum
```
3. Crack a hash file with John the Ripper using a wordlist:
```bash
john --wordlist=/usr/share/wordlists/rockyou.txt hashes.txt
```
4. Crack with Hashcat (mode 0 = MD5, adjust per hash type):
```bash
hashcat -m 0 -a 0 hashes.txt /usr/share/wordlists/rockyou.txt
```
5. Test a login form for weak credentials (lab target only):
```bash
hydra -l admin -P /usr/share/wordlists/rockyou.txt 10.0.5.15 http-post-form "/login:user=^USER^&pass=^PASS^:F=incorrect"
```

### Verify Install
```bash
john --version
hashcat --version
hydra -h
```

### Rules of Engagement
- Only crack hashes/credentials you own or are explicitly authorized to test.
- Brute-forcing live login forms outside a lab is illegal without written permission — this can also lock out real accounts.

### Checklist
- [ ] Cracking tools installed
- [ ] Cracked a self-generated test hash
- [ ] Understand difference between hashing and encryption
- [ ] Tested MFA/lockout behavior on a lab login form
