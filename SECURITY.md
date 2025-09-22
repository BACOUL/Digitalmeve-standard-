# Security Policy — DigitalMeve

DigitalMeve takes security with the utmost seriousness.  
Our mission is to provide a **global standard for invisible proofs and certified files** — privacy-first, tamper-proof, and interoperable.  
This document describes how to report vulnerabilities, how we handle them, and the scope of our security program.

---

## 📌 Scope

The following assets are covered by this policy:

- **DigitalMeve Standard** (`.meve` certified files such as `.pdf`, `.docx`, `.jpg`).
- **DigitalMeve Certificates** (HTML-based signed proofs).
- **DigitalMeve Website & Services** (`digitalmeve.com`, verification portal, file protection portal).
- **Payment & Subscription System** (Stripe integration for Individuals & Professionals).
- **Developer Tooling** (future APIs, SDKs, CLI).

Out of scope:
- Personal environment or browser configuration issues.
- Denial-of-Service (DoS) attacks without proof of exploitability.
- Spam, phishing, or social engineering against staff or users.
- Visual/UI issues that do not impact integrity or confidentiality.

---

## 🔐 Reporting a Vulnerability

If you discover a vulnerability, please **do not create a public GitHub Issue**.  
Instead, report it privately:

- 📧 Email: **security@digitalmeve.org**
- 🔑 GPG Key: [Public Key Download](https://digitalmeve.org/pgp-key.txt) (use to encrypt sensitive reports)

Please include:
- A detailed description of the vulnerability.
- Steps to reproduce (proof of concept if possible).
- Impact assessment (which component, severity, potential misuse).
- Suggested fix (optional, but appreciated).

---

## ⏱ Response Timeline

- **Acknowledgement**: within **48 hours** of receiving the report.  
- **Initial assessment**: within **5 business days** (CVE severity rating if applicable).  
- **Fix or mitigation**: within **30 days** for critical/high vulnerabilities.  
- **Disclosure**: coordinated with the reporter once the patch is deployed.

---

## ✅ Responsible Disclosure Policy

- Please give us a **reasonable time** (30 days) to fix the issue before public disclosure.  
- Do not exploit or weaponize the vulnerability beyond what is necessary to prove it.  
- We will credit security researchers who follow this policy in our **Hall of Fame**.  
- We will never pursue legal action against good-faith, responsible disclosure.

---

## 🛡 Compliance & Security Principles

DigitalMeve aligns with **global best practices**:

- **GDPR** (EU) & **CCPA** (California) — user privacy guaranteed.  
- **PCI DSS / PSD2** — for all Stripe payment integrations.  
- **ISO 27001 principles** — information security management.  
- **Cryptographic best practices**:
  - SHA-256 invisible fingerprint inside every certified file.
  - DigitalMeve invisible key embedded per file.
  - Visible watermark for transparency.
  - Private enterprise keys for Professional plans.
- **Defense in Depth**:
  - TLS 1.3 everywhere.
  - Zero server storage for user files (all processing is client-side).
  - Regular penetration testing and dependency scans.

---

## 🏆 Recognition Program

We recognize the contribution of security researchers who help keep DigitalMeve safe.  
If you responsibly disclose a vulnerability and it is confirmed, you may be added to our **Security Hall of Fame**.

Hall of Fame will be published here:  
👉 [digitalmeve.org/security/hall-of-fame](https://digitalmeve.org/security/hall-of-fame)

---

## ⚖️ Legal Safe Harbor

- DigitalMeve will not pursue legal action against researchers who follow this policy in good faith.  
- Security testing must be **non-disruptive** and avoid affecting real users.  
- Safe Harbor applies worldwide.

---

## 📬 Contact

- Email: [security@digitalmeve.org](mailto:security@digitalmeve.org)  
- GPG Key: [digitalmeve.org/pgp-key.txt](https://digitalmeve.org/pgp-key.txt)  
- Website: [https://digitalmeve.com](https://digitalmeve.com)

---

**DigitalMeve — Invisible Proof. Visible Trust.**  
Together, we build a global security standard.
