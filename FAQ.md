# FAQ — DigitalMeve

DigitalMeve is the global standard for invisible, tamper-proof certification of digital files. This FAQ addresses developers, professionals, and individual users.

---

## Table of Contents
1. What is DigitalMeve?
2. How does the invisible proof work?
3. What types of files are supported?
4. What information is embedded in a certificate?
5. How do I verify a certified file?
6. Does DigitalMeve store my files?
7. Is DigitalMeve compliant with GDPR and other data protection laws?
8. How secure is DigitalMeve?
9. What is the difference between free, individual, and professional plans?
10. Can I integrate DigitalMeve into my app or workflow?
11. How does DNS binding work for professionals?
12. What happens if DigitalMeve disappears?
13. How does DigitalMeve handle payments?
14. What if I cancel my subscription?
15. What if I am a developer and want to contribute?
16. Can governments or regulators use DigitalMeve?
17. How future-proof is the cryptography?
18. Who governs the DigitalMeve standard?

---

## 1. What is DigitalMeve?
DigitalMeve is a global standard for embedding invisible, tamper-proof certificates into any file (PDF, DOCX, JPG, MP4, etc.). It ensures authenticity and integrity without exposing private data.

---

## 2. How does the invisible proof work?
Each certified file includes:
- A **visible watermark** (optional, depending on plan).
- An **invisible SHA-256 hash** integrated into the document.
- An **invisible DigitalMeve key** to bind the certification.
- For paying users: metadata (name/email or company reference).
- For professionals: signatures with enterprise private keys + DNS binding.

This proof cannot be altered without invalidating the file.

---

## 3. What types of files are supported?
All major formats:
- Documents: PDF, DOCX, TXT
- Images: JPG, PNG
- Media: MP4, WAV
- Archives: ZIP
DigitalMeve is format-agnostic: if you can open it, you can certify it.

---

## 4. What information is embedded in a certificate?
Depending on plan:
- **Free**: watermark + SHA-256
- **Individuals**: watermark + SHA-256 + invisible key + certificate with name/email
- **Professionals**: watermark + SHA-256 + enterprise key + DNS binding + branded certificate

---

## 5. How do I verify a certified file?
Drag and drop the file into the [Verify tool](https://digitalmeve.com/verify). Verification runs entirely in your browser, no upload required.

---

## 6. Does DigitalMeve store my files?
No. DigitalMeve is privacy-first:
- Processing runs locally in the browser.
- No file storage.
- Only metadata necessary for certificates is embedded within the file itself.

---

## 7. Is DigitalMeve compliant with GDPR and other data protection laws?
Yes. Compliance includes:
- GDPR (EU)
- CCPA (California)
- PSD2 / PCI DSS (Stripe payments)
- ISO 27001 principles
No personal data is shared without user consent.

---

## 8. How secure is DigitalMeve?
- Based on proven cryptography (SHA-256, elliptic curves).
- Independent verification: no hidden servers or lock-in.
- Certificates cannot be forged or altered without detection.

---

## 9. What is the difference between free, individual, and professional plans?
- **Free**: 5 certified files/month.
- **Individuals**: €9.90/month or €99/year → unlimited files, named certificate.
- **Professionals**: €29.90/month or €299/year → unlimited files, enterprise private key, DNS binding, branded certificates.

---

## 10. Can I integrate DigitalMeve into my app or workflow?
Yes. An API and SDKs are planned (see Roadmap v2). Current workflows use the web app.

---

## 11. How does DNS binding work for professionals?
Professional subscribers can bind their domain (e.g., `company.com`) to their DigitalMeve key, so every certified file can be verified as belonging to that domain.

---

## 12. What happens if DigitalMeve disappears?
DigitalMeve is designed as an open standard:
- Certificates remain valid without servers.
- Verification code is open source.
- Any developer can build independent verifiers.

---

## 13. How does DigitalMeve handle payments?
Payments are handled via **Stripe** with full PCI DSS compliance. Pricing adapts to local currencies based on location.

---

## 14. What if I cancel my subscription?
- You keep all previously certified files: they remain valid forever.
- You lose the ability to generate new certificates beyond the free tier.

---

## 15. What if I am a developer and want to contribute?
- Open issues or pull requests on GitHub.
- Follow [CONTRIBUTING.md](./CONTRIBUTING.md).
- Major changes must include an ADR (Architecture Decision Record).

---

## 16. Can governments or regulators use DigitalMeve?
Yes. Governments, universities, and institutions can:
- Certify diplomas, legal documents, licenses.
- Issue enterprise keys for public use.
DigitalMeve’s governance ensures neutrality and long-term support.

---

## 17. How future-proof is the cryptography?
Roadmap includes:
- Post-quantum cryptography (v3).
- Optional blockchain anchoring.
- Continuous security audits.

---

## 18. Who governs the DigitalMeve standard?
Governance is open and transparent:
- Decisions recorded in `/ADRs`.
- Community-driven contributions via GitHub.
- Mandatory audits for security-related changes.
- Long-term stewardship to ensure neutrality.

---
