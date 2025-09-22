# DigitalMeve Standard Specification (v1.0)

> **Status:** Draft Standard (v1.0)  
> **License:** CC BY 4.0 (specification only)  
> **Maintainer:** DigitalMeve Core Team  
> **Scope:** Universal proof & certification for digital files (.MEVE)

---

## 1. Introduction
DigitalMeve defines a universal method for certifying and verifying digital files with **proofs that are both human-visible and machine-verifiable**.  
It is designed to be lightweight, privacy-first, and interoperable across all file types.  

DigitalMeve combines:
- **Visible watermark** → human recognition
- **Invisible cryptographic token** → SHA-256 hash bound to file
- **DigitalMeve hidden key** → embedded invisible reference for universal validation
- **Optional nominative certificate** → name or email of certifier (for paying individuals)
- **Private key signature** → for enterprises, tied to company identity

---

## 2. Goals
- **Universal** → Works with any file format (.pdf, .docx, .png, etc.)
- **Decentralized verification** → Proofs verifiable offline, without servers
- **Privacy-first** → No file upload required (in-browser processing)
- **Future-proof** → Cryptographic agility (post-quantum readiness)
- **Accessible** → Free tier, individual tier (€9.90), professional tier (€29.90)

---

## 3. Terminology
- **.MEVE Proof**: Bundle of cryptographic elements (visible + invisible) embedded in a file.  
- **Certificate**: Publicly readable `.meve.certificate.html` file containing metadata and cryptographic bindings.  
- **Invisible token**: SHA-256 hash + DigitalMeve hidden key, embedded without altering usability.  
- **Enterprise Key**: Private key issued to professional subscribers for enterprise-level signing.

---

## 4. Threat Model
DigitalMeve resists:
- File tampering (SHA-256 integrity)
- Unauthorized duplication (proof breaks if modified)
- Identity fraud (nominative certificate & enterprise key)
- Longevity risks (crypto agility + algorithm upgrade plan)

---

## 5. Proof Model
Every certified file contains:
1. **Visible watermark**: “Certified by DigitalMeve” + unique hash fragment  
2. **Invisible SHA-256 hash**: full fingerprint of file content  
3. **Invisible DigitalMeve token**: secret marker enabling universal recognition  
4. **Optional nominative field**: name/email of paying individual  
5. **Enterprise signature**: digital signature with enterprise private key  

Certificate file (`.meve.certificate.html`) includes:
- File hash (SHA-256)
- Timestamp (UTC)
- Proof metadata (watermark location, invisible token presence)
- Certifier identity (if applicable)
- Enterprise signature block (if applicable)

---

## 6. Cryptography
- **Hashing**: SHA-256 (default), SHA3-512 optional  
- **Signature (Enterprise)**: Ed25519 (v1), Post-Quantum ready (Dilithium, v2)  
- **Randomness**: NIST SP 800-90A DRBG  
- **Encoding**: Base58 for compact proofs  
- **Future-proofing**: All certificates carry an `alg` field for upgrade compatibility  

---

## 7. File Support
DigitalMeve is format-agnostic:  
- PDF, DOCX → watermark embedded, invisible tokens in metadata  
- PNG, JPG → watermark overlay, invisible tokens in EXIF  
- TXT, MD → watermark comment block, invisible tokens in hidden metadata  

---

## 8. Privacy & Data Protection
- All processing in-browser (WebAssembly runtime)  
- No files uploaded unless user explicitly shares  
- GDPR, CCPA, ISO/IEC 27001 compliant storage (for paying tiers)  
- Stripe used for payments (PCI-DSS Level 1)  
- Certificates contain **only minimal metadata** (no hidden PII unless opted-in)  

---

## 9. Verification Flow
Verification can be performed:
- **Offline** → with certificate `.html` + file  
- **Online** → via DigitalMeve verifier page (open-source client)  
- **Enterprise integration** → DNS binding (`/.well-known/meve.json`)  

Steps:
1. Load file  
2. Extract invisible token & SHA-256  
3. Compare with certificate  
4. Verify optional nominative / enterprise signature  
5. Output: Valid / Invalid / Expired  

---

## 10. Pricing & Access
- **Free tier** → watermark + invisible SHA-256 + invisible token  
- **Individual tier (€9.90/month or €99/year)** → nominative certificate (name/email)  
- **Professional tier (€29.90/month or €299/year)** → enterprise private key, bulk workflow, API integration  
- Prices adapt to local purchasing power (regional adjustment)  
- Payments via Stripe (PCI-DSS compliant)  
- Refund policy aligned with EU Consumer Rights & global standards  

---

## 11. Governance
- **Spec ownership**: Open standard, CC BY 4.0  
- **Implementation**: DigitalMeve reference stack (commercial license)  
- **Change process**: Architecture Decision Records (ADRs) + public PRs  
- **Versioning**: Semantic Versioning (SemVer)  
- **Cryptographic agility**: Reserved extension field in certificates  

---

## 12. Compliance & References
DigitalMeve aligns with:
- **ISO/IEC 27001** (security management)  
- **ISO/IEC 22301** (resilience)  
- **ETSI EN 319 102** (electronic signatures)  
- **eIDAS (EU)**  
- **NIST SP 800-57** (crypto lifetimes)  
- **GDPR / CCPA**  

---

## 13. Roadmap
- **v1.0** → SHA-256 + Ed25519 + HTML certificates  
- **v1.1** → Bulk workflows + API + enterprise DNS bindings  
- **v2.0** → Post-quantum crypto + multi-language clients  
- **v3.0** → Full ISO submission as a recognized digital certification standard  

---

## Appendix A: Example Certificate (simplified)
```html
<!DOCTYPE html>
<html>
<head><meta charset="utf-8"><title>DigitalMeve Certificate</title></head>
<body>
  <h1>DigitalMeve Certificate</h1>
  <p>File: contract.pdf</p>
  <p>Hash (SHA-256): ab34f9...e91c</p>
  <p>Issued: 2025-09-22T14:02:00Z</p>
  <p>Certifier: john.doe@example.com</p>
  <p>Enterprise Signature: [Ed25519-Signature]</p>
</body>
</html>
