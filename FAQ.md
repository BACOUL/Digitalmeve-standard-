# DigitalMeve – Frequently Asked Questions (FAQ)

_Last updated: 2025-09-22_

---

## 1. General

**Q: What is DigitalMeve in one sentence?**  
A: DigitalMeve is the open global standard for certifying digital files — embedding invisible cryptographic proofs directly inside documents, while keeping them private, portable, and universally verifiable.

**Q: How is DigitalMeve different from a signed PDF or traditional timestamping?**  
A: Unlike static signatures or external timestamps, DigitalMeve integrates:  
- A visible watermark (for universal recognition).  
- An invisible SHA-256 fingerprint embedded inside the file.  
- An invisible DigitalMeve proof key.  
This makes the proof tamper-evident, device-independent, and long-lasting — without depending on centralized storage.

**Q: Is DigitalMeve really an open standard?**  
A: Yes. The specification is public, versioned, and governed through community feedback and **Architecture Decision Records (ADRs)**. Anyone can implement a generator or verifier.

---

## 2. For Individuals

**Q: How much does it cost?**  
A: 9.90 €/month or annual subscription with discount. Prices are adjusted per region/country following Stripe standards and local regulations.

**Q: Are my files stored by DigitalMeve?**  
A: No. All processing happens locally in your browser or client. We never upload, retain, or index your files.

**Q: Can I cancel or request a refund?**  
A: Yes. Subscriptions can be canceled anytime. Refunds follow Stripe and consumer protection standards (e.g. 14-day withdrawal in the EU).

**Q: Can I certify personal files like CVs, invoices, photos or artworks?**  
A: Absolutely. The Individual plan is designed for creators, freelancers, students, and anyone who needs personal digital proof.

**Q: Will my name or email appear in the certificate?**  
A: Yes, if you are a paying individual subscriber, your identifier (name or email) will be embedded in the certificate for traceability.

---

## 3. For Professionals

**Q: What’s the difference between Individual and Pro plans?**  
A: Pro (29.90 €/month or annual) includes:  
- Private company key for signing at organization level.  
- Visible watermark + invisible proof + enterprise certificate.  
- Workflow integration (ERP, CRM, CMS).  
- Bulk certification support.  
- Priority support and compliance documentation.

**Q: How does the company private key work?**  
A: Each enterprise account receives a unique cryptographic keypair. The private key is used to sign files under the company identity; the public key is distributed for universal verification.

**Q: Can I integrate DigitalMeve into my workflows?**  
A: Yes. APIs and CLI tools are provided for bulk operations, automation, and system integration.

**Q: Which file types are supported?**  
A: DigitalMeve works with all major formats: PDF, DOCX, XLSX, PNG, JPG, MP4, and others. The proof layer is format-agnostic.

**Q: Is DigitalMeve legally compliant?**  
A: Yes. It aligns with **eIDAS (EU), GDPR, ISO 27001, and global cryptographic best practices**. Enterprise customers can request compliance reports.

---

## 4. Technical & Security

**Q: What cryptographic algorithms are used?**  
A: SHA-256 for fingerprints, elliptic curve cryptography for signatures, and TLS/HTTPS for transport. Algorithms are modern, auditable, and regularly reviewed.

**Q: What happens if a file is modified after certification?**  
A: Any modification invalidates the embedded SHA-256 fingerprint. Verification will fail, clearly signaling tampering.

**Q: How long are DigitalMeve certificates valid?**  
A: Indefinitely. Proofs are self-contained and do not depend on external servers.

**Q: Can I verify without your website?**  
A: Yes. We provide open-source verification tools (CLI and libraries). Anyone can confirm authenticity offline.

**Q: What exactly is in a `.meve.html` certificate?**  
A: A human-readable HTML containing the proof metadata, embedded cryptographic signature, and links for independent verification. Sensitive implementation details remain private.

---

## 5. Privacy & GDPR

**Q: Do you collect my files?**  
A: No. Files never leave your device.

**Q: Do you comply with GDPR and global privacy laws?**  
A: Yes. DigitalMeve is built with privacy by design. No personal data is processed beyond what is necessary for billing (via Stripe).

**Q: Where is data processed?**  
A: Payments and minimal account data are processed by Stripe with data residency in the EU/US depending on user location. Files remain local.

**Q: What if I want to delete my data?**  
A: You can request deletion at any time. We comply with GDPR Article 17 (right to erasure).

---

## 6. Payment & Billing

**Q: What payment methods are supported?**  
A: Stripe supports major credit/debit cards, Apple Pay, Google Pay, SEPA, and others depending on your region.

**Q: Do you support crypto payments?**  
A: Not at launch, but this is under consideration.

**Q: How does annual billing work?**  
A: You can choose annual payment upfront (with discount) or monthly recurring billing.

**Q: What is your refund policy?**  
A: Refunds are processed in line with consumer law and Stripe’s global standards.

---

## 7. Standard & Community

**Q: How can I contribute to the standard?**  
A: Contributions are welcome via GitHub pull requests. Changes must follow the **CONTRIBUTING.md** guidelines and ADR process.

**Q: What are ADRs?**  
A: Architecture Decision Records document major technical decisions, ensuring traceability and accountability over time.

**Q: Who governs DigitalMeve?**  
A: A lightweight governance model with maintainers, ADR reviewers, and community input. Transparency and neutrality are key principles.

**Q: Can other companies adopt DigitalMeve?**  
A: Yes. The standard is open and royalty-free. Companies can integrate or extend DigitalMeve in their products without restriction.

---

## 8. Support

- 📧 Email: support@digitalmeve.org  
- 🌐 Website: [digitalmeve.org](https://digitalmeve.org)  
- 🐙 GitHub: [github.com/digitalmeve](https://github.com/digitalmeve)  

---

> DigitalMeve is committed to being the **global reference for digital file certification**: invisible, private, universal.
