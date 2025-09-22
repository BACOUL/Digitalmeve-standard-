# FAQ — DigitalMeve

A structured FAQ for individuals, professionals, and developers.  
DigitalMeve is building the global standard for invisible proof and visible trust.

---

## 1. General Questions

**Q: What is DigitalMeve?**  
DigitalMeve is a global standard for file certification. It embeds invisible cryptographic proofs inside your documents while generating a verifiable certificate you can share. Proofs are **universal, transparent, and privacy-first**.

**Q: Is it free to use?**  
Yes. Individuals can certify up to **5 files per month** for free. Paid subscriptions unlock higher limits and professional features.

**Q: Do you store my files?**  
No. Files are processed **entirely in your browser**. DigitalMeve never stores, uploads, or has access to your files.

**Q: What file types are supported?**  
All file types. Certificates are format-agnostic: PDF, DOCX, PNG, MP4, ZIP, etc.

**Q: How is this different from a PDF signature or blockchain?**  
- PDF signatures are format-specific; DigitalMeve is universal.  
- Blockchains are heavy and public; DigitalMeve is light, private, and works offline.  
- DigitalMeve combines **visible watermark + invisible cryptographic anchors**.

---

## 2. For Individuals

**Q: How many documents can I certify for free?**  
Up to **5 documents per month**. Each document receives a verifiable DigitalMeve certificate.

**Q: What happens if I exceed the free limit?**  
You can subscribe to **DigitalMeve Individual** (9.90 €/month or yearly equivalent) to certify unlimited documents under your personal identity (name or email).

**Q: What information is included in my certificate?**  
- File name and SHA-256 hash  
- Timestamp (UTC)  
- Certificate ID  
- Issuer type (anonymous, personal, or professional)  
- Invisible watermark embedded in your file  

**Q: Can I use DigitalMeve certificates in legal disputes?**  
Yes. Certificates are based on cryptographic proofs (SHA-256) and timestamped, which are widely accepted in legal and compliance contexts. Legal validity may vary by jurisdiction.

---

## 3. For Professionals & Enterprises

**Q: How does DNS-based certification work?**  
Professional domains can publish a `.well-known/meve.json` file. This binds your domain name to your DigitalMeve certificates, proving authenticity at the organizational level.

**Q: How are private keys generated and used?**  
Each Pro/Enterprise account receives a **dedicated private key** for signing certificates. Keys never leave the user’s device; they are generated and stored locally or in HSM-compliant modules.

**Q: Can I automate bulk certification (API/SDK)?**  
Yes. Pro and Enterprise plans include API endpoints and SDKs to certify thousands of files within workflows.

**Q: Is the service compliant with audit/legal standards?**  
Yes. DigitalMeve follows **ISO 27001**, **GDPR**, and payment industry standards (PCI-DSS). Certificates are auditable and designed to be court-admissible.

**Q: How do subscription and billing work?**  
- **Pro plan**: 29.90 €/month or yearly equivalent.  
- **Enterprise**: custom pricing with SLA, API scaling, and advanced security features.  
- Payments are processed via **Stripe**, fully compliant with global payment regulations.

---

## 4. For Developers

**Q: How do I verify a `.MEVE` certificate programmatically?**  
Certificates are JSON-based and can be verified with a single command (`meve verify`) or by importing our SDK.

**Q: Is there an SDK or API available?**  
Yes. SDKs are available in **JavaScript/TypeScript**, with Python and Go in progress. REST API endpoints are documented in the developer portal.

**Q: What does the certificate format look like?**  
Certificates are structured JSON objects, including:  
- File hash (SHA-256)  
- Metadata (timestamp, issuer type)  
- Verification anchors (DNS, optional signatures)  

**Q: How are updates to the standard managed?**  
All changes follow **Architecture Decision Records (ADRs)**. Updates are versioned (semver) and publicly discussed on GitHub.

**Q: Can I embed verification inside my app/site?**  
Yes. Verification libraries are lightweight (<50kb) and can run client-side without servers.

---

## 5. Security & Privacy

**Q: What is embedded in the document?**  
- **Visible watermark** (DigitalMeve Certified)  
- **Invisible SHA-256 digest** embedded in metadata  
- **Invisible DigitalMeve key** (unique anchor)  

**Q: How secure is the SHA-256 hashing?**  
SHA-256 is an industry-standard cryptographic hash function, considered collision-resistant. It is trusted globally for integrity proofs.

**Q: What happens if my private key is compromised?**  
Keys can be revoked. Revocation lists are published by DigitalMeve and checked during verification.

**Q: Is DigitalMeve GDPR-compliant?**  
Yes. No personal data is stored unless you opt in (e.g. pro subscription). All data is encrypted in transit and processed locally.

**Q: How are payments secured?**  
Payments are handled by **Stripe** with PCI-DSS compliance. DigitalMeve never stores card details.

---

## 6. Support & Community

**Q: How can I report a bug or vulnerability?**  
Use the [GitHub Security Policy](./SECURITY.md) or email **security@digitalmeve.com**. Responsible disclosure is required.

**Q: Can I become an early partner?**  
Yes. Apply via the [Early Partner Program](./PARTNERS.md) to test integrations and influence the roadmap.

**Q: How do I contribute to the standard?**  
- Fork the repo  
- Open a Pull Request with an ADR  
- Follow the [CONTRIBUTING.md](./CONTRIBUTING.md) guidelines  

**Q: Where can I find updates and the roadmap?**  
Roadmap is public in [ROADMAP.md](./ROADMAP.md). Announcements are posted on GitHub and the DigitalMeve newsletter.

---

📌 **Reminder:** DigitalMeve does not replace legal advice. Always check local regulations before relying on certificates for compliance or litigation.
