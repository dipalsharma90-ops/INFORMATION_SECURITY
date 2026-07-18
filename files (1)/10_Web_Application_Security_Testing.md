# Topic 10: Web Application Security Testing

### Goal
Identify and understand common web vulnerabilities (OWASP Top 10) using a proxy and a deliberately vulnerable app.

### Core Tools
| Tool | Purpose |
|---|---|
| Burp Suite Community | Intercepting proxy |
| OWASP ZAP | Free web app scanner/proxy |
| sqlmap | Automated SQL injection testing |
| DVWA | Practice target application |

### Setup Steps
1. Deploy DVWA in your lab (Docker method):
```bash
docker run --rm -it -p 80:80 vulnerables/web-dvwa
```
2. Configure your browser to route traffic through Burp Suite's proxy (default `127.0.0.1:8080`).
3. Browse DVWA through the proxy and capture a login request in Burp's **Proxy > HTTP history**.
4. Test for SQL injection on a vulnerable parameter:
```bash
sqlmap -u "http://10.0.5.15/dvwa/vulnerabilities/sqli/?id=1" --cookie="PHPSESSID=xxx; security=low" --batch
```
5. Test for reflected XSS by injecting a harmless payload into an input field:
```
<script>alert('test')</script>
```

### Verify Install
```bash
docker --version
sqlmap --version
```

### Rules of Engagement
- Only test DVWA/lab apps you deployed yourself — never run sqlmap or XSS payloads against real, non-authorized websites.

### Checklist
- [ ] DVWA (or similar) deployed locally
- [ ] Intercepted and inspected traffic with Burp/ZAP
- [ ] Demonstrated one SQLi finding in the lab app
- [ ] Demonstrated one XSS finding in the lab app
