# Security Policy

## Supported Versions

DigitalMeve is under **continuous development**. Security updates are provided for the following branches:

| Version      | Supported |
|--------------|------------|
| Main (`main`)| ✅ Always |
| Releases ≥ v1.0.0 | ✅ Supported |
| Pre-release / Experimental branches | ❌ Not guaranteed |

If you are using an **unsupported branch**, please upgrade to the latest stable version to continue receiving security updates.

---

## Reporting a Vulnerability

We take security issues very seriously.  
If you discover a vulnerability in **DigitalMeve**, please report it responsibly:

- **Private email**: [security@digitalmeve.org](mailto:security@digitalmeve.org)  
- **Do NOT** open a public GitHub issue for security problems.  
- Include as much detail as possible:
  - Steps to reproduce the vulnerability  
  - Affected versions or configurations  
  - Possible impact and severity  
  - Suggested mitigations (if any)  

We aim to acknowledge all reports within **72 hours** and provide a remediation plan within **7 working days**.

---

## Disclosure Process

1. **Triage**  
   - Security team reviews the report and assesses severity (CVSS scoring).  
   - Assigns a tracking ID.  

2. **Fix**  
   - Developers work on a private branch to fix the issue.  
   - Additional security audits may be performed.  

3. **Release**  
   - A patched version is released.  
   - Security advisories are published on GitHub and [digitalmeve.org/security](https://digitalmeve.org/security).  

4. **Disclosure**  
   - Once the fix is released, we credit the reporter (if desired).  
   - A CVE may be requested and assigned.  

---

## Scope of Security Issues

Examples of issues we consider **in scope**:
- Cryptographic vulnerabilities (hashing, signatures, invisible watermarking)  
- Certificate or proof forgery  
- Insecure storage or leakage of private keys  
- Authentication/authorization flaws  
- Supply chain or dependency risks  

Examples of issues **not in scope**:
- Bugs not affecting security (UI glitches, typos)  
- Vulnerabilities in dependencies not maintained by DigitalMeve (but we may forward)  
- Denial of Service (DoS) via extreme inputs, unless critical  

---

## Coordinated Disclosure

We follow a **Coordinated Vulnerability Disclosure (CVD)** model:  
- We ask reporters to keep vulnerabilities **private** until a fix is released.  
- We commit to transparency once users are protected.  
- DigitalMeve may grant **bug bounty rewards** (future program) for valid high-severity reports.  

---

## Security Best Practices for Users

To protect your own usage of DigitalMeve:

- Always use the **latest version** of the software  
- Verify `.MEVE` certificates only via trusted sources  
- For enterprises:  
  - Use your private keys securely  
  - Rotate signing keys regularly  
  - Enforce internal policies for certificate issuance  

---

## Contact

- Security email: [security@digitalmeve.org](mailto:security@digitalmeve.org)  
- Emergency contact: see [GOVERNANCE.md](GOVERNANCE.md)  

For all security-related communications, **encryption (PGP)** is available.  
Fingerprint and public key are published at: [digitalmeve.org/pgp](https://digitalmeve.org/pgp)

---

## Attribution

This policy is inspired by security practices of:
- [GitHub Security Policy](https://docs.github.com/en/code-security/security-advisories)  
- [Kubernetes Security Response Committee](https://kubernetes.io/security/)  
- [CNCF Security Guidelines](https://github.com/cncf/foundation/blob/main/security)  

Adapted to the unique mission of **DigitalMeve** as a **global standard of invisible proof and certification**.
