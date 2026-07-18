# Topic 15: Security Audit and Best Practices

### Goal
Evaluate an environment's overall security posture against a recognized standard and produce a remediation roadmap.

### Core Tools
| Tool | Purpose |
|---|---|
| CIS-CAT / Lynis | Automated security baseline auditing |
| ISO 27001 / NIST CSF checklists | Audit frameworks |
| OpenSCAP | Compliance scanning |

### Setup Steps
1. Install Lynis for a quick local security audit:
```bash
sudo apt install lynis -y
sudo lynis audit system
```
2. Review the generated report for warnings and suggestions:
```bash
cat /var/log/lynis-report.dat
```
3. Cross-check findings against a checklist (e.g., CIS Benchmarks) for your OS.
4. Prioritize fixes: patch management, unused services, weak permissions, missing MFA.
5. Document a remediation roadmap with owners and target dates for each finding.

### Verify Install
```bash
lynis --version
```

### Rules of Engagement
- Audits should be repeated periodically (e.g., quarterly) — security posture drifts over time as systems and configs change.

### Checklist
- [ ] Ran an automated audit tool (Lynis/OpenSCAP)
- [ ] Reviewed findings against a recognized framework
- [ ] Produced a prioritized remediation roadmap
- [ ] Scheduled a recurring audit cadence

---

*Each topic above is written as a hands-on lab module. Work through them in order — later topics (scanning, web testing, incident response) assume the lab environment from Topics 1–3 is already set up.*
