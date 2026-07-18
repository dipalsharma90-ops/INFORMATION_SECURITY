# Topic 9: Cryptography Fundamentals

### Goal
Understand symmetric/asymmetric encryption, hashing, and how TLS certificates secure real traffic.

### Core Tools
| Tool | Purpose |
|---|---|
| OpenSSL | Encryption, certificates, hashing CLI |
| GPG | File/message encryption and signing |
| `sha256sum` / `md5sum` | Quick hash generation |

### Setup Steps
1. Generate an AES-encrypted file (symmetric):
```bash
openssl enc -aes-256-cbc -salt -in secret.txt -out secret.enc
openssl enc -d -aes-256-cbc -in secret.enc -out secret_decrypted.txt
```
2. Generate an RSA key pair (asymmetric):
```bash
openssl genrsa -out private.pem 2048
openssl rsa -in private.pem -pubout -out public.pem
```
3. Hash a file to check integrity:
```bash
sha256sum document.pdf
```
4. Create a self-signed TLS certificate (for lab HTTPS testing):
```bash
openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -days 365
```
5. Inspect a live site's certificate chain:
```bash
openssl s_client -connect example.com:443 -showcerts
```

### Verify Install
```bash
openssl version
gpg --version
```

### Rules of Engagement
- Self-signed certs are for lab/testing only — browsers will flag them as untrusted, which is expected.

### Checklist
- [ ] Encrypted and decrypted a file symmetrically
- [ ] Generated an RSA key pair
- [ ] Hashed a file and understood its purpose (integrity, not secrecy)
- [ ] Created and inspected a self-signed certificate
