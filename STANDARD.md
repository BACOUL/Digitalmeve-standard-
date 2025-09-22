DigitalMeve Standard (DMS)

Invisible proof. Visible trust.
The global standard for embedding invisible, tamper-proof certificates into any digital file.
Files remain private — verification is universal.


---

📖 Table of Contents

1. Introduction

2. Terminology

3. Goals

4. Certificate Structure

5. Certification Flow

6. Security Layers

7. Payment Tiers

8. Compliance

9. Extensibility

10. Governance

11. Examples

12. License



---

1. Introduction

The DigitalMeve Standard (DMS) defines a universal certificate format that can be invisibly embedded into any digital file.
Its mission is to make every file globally verifiable, without servers, while ensuring privacy, simplicity, and long-term trust.


---

2. Terminology

Certificate → The invisible proof generated and bound to a file.

Visible watermark → Optional overlay (logo, code, or discreet text).

Invisible SHA-256 hash → Cryptographic integrity check, embedded in the file.

Invisible DigitalMeve key → Proprietary invisible marker for universal verification.

Private key → Enterprise-only cryptographic key used to sign documents.

Certificate Authority (CA) → The role of DigitalMeve in issuing certificates.



---

3. Goals

Privacy-first → Files never leave the user’s device.

Universal → Works with any file type (PDF, DOCX, JPG, PNG, MP4…).

Trust at scale → Suitable for individuals, professionals, and enterprises.

Future-proof → Post-quantum algorithms and new formats supported.



---

4. Certificate Structure

Every DigitalMeve-certified file includes:

✅ Visible watermark → Basic layer of deterrence.

✅ Invisible SHA-256 hash → Guarantees file integrity.

✅ Invisible DigitalMeve key → Unique identifier for global validation.

✅ Metadata (tier-specific):

Free → Anonymous proof.

Individuals (paid) → Name or email included in the certificate.

Professionals → Enterprise private key signature + DNS binding.




---

5. Certification Flow

Generate:

1. User uploads or drags a file into the generator (processed on-device).


2. File is watermarked and invisible data is embedded.


3. A certificate (HTML format) is issued, containing metadata and verification link.



Verify:

1. User drags & drops a file into the verifier.


2. SHA-256 and DigitalMeve key are extracted.


3. Validity is shown in seconds: ✅ Authentic / ❌ Tampered.




---

6. Security Layers

🔒 Visible watermark → Immediate human-visible proof.

🔑 SHA-256 hash → Strong integrity check.

🧩 DigitalMeve invisible key → Proprietary invisible marker.

🏢 Enterprise private keys → Company identity proof.

🌐 DNS binding → Confirms organization’s domain ownership.



---

7. Payment Tiers

Free → 5 files/month, anonymous certificate.

Individuals → €9.90/month (or yearly discount), unlimited files, personal identity in certificate.

Professionals → €29.90/month (or yearly discount), unlimited files, enterprise key, DNS binding, branded watermark.


👉 See Pricing for details.


---

8. Compliance

DigitalMeve is aligned with:

GDPR (EU) & CCPA (California).

PSD2 & PCI DSS (Stripe payments).

ISO 27001 principles.

Roadmap includes post-quantum cryptography for resilience.


👉 See Security Model.


---

9. Extensibility

Enterprise dashboards & APIs.

Audit logs for compliance.

Blockchain anchoring for long-term persistence.

Support for new formats and quantum-safe algorithms.



---

10. Governance

Transparent decision-making through ADRs (Architecture Decision Records).

Community proposals via pull requests.

Security-critical changes require audits.

Semantic versioning applies (MAJOR.MINOR.PATCH).


👉 See Governance.


---

11. Examples

📄 Sample certificate (PDF)

🌐 DNS binding example

✅ Verification data



---

12. License

Documentation → CC BY 4.0

Reference implementations → MIT License



---
