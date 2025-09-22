# DigitalMeve Standard Specification (.MEVE)

**Version:** 1.0  
**Status:** Draft for public review  
**Authors:** DigitalMeve Working Group  
**License:** CC BY 4.0  

---

## 1. Purpose and Scope
The `.MEVE` certificate is a **universal, lightweight proof container** designed to certify the integrity and authenticity of any digital file.  

Goals:
- Ensure **trust** without central servers.  
- Enable **instant verification** by anyone, anywhere.  
- Provide a **future-proof open standard** for individuals, professionals, and organizations.  

The `.MEVE` format is intended to become the **global standard for digital file certification**, comparable to how PDF became the standard for documents.

---

## 2. Terminology
- **Certificate**: The `.meve.json` file containing the proof.  
- **Issuer**: The entity (individual or professional) generating the proof.  
- **Verifier**: Any party validating a `.MEVE` certificate.  
- **Binding**: Optional DNS-based mechanism linking certificates to a domain.  
- **.MEVE version**: The specification version used to generate the certificate.  

---

## 3. Core Principles
1. **Privacy-first** → files never leave the device.  
2. **Independent verification** → no central authority required.  
3. **Cryptographic integrity** → based on modern, auditable algorithms.  
4. **Universal compatibility** → works with any file type.  
5. **Durability** → valid across time, devices, and formats.  
6. **Transparency** → open, vendor-neutral, auditable.  

---

## 4. File Format Definition

A `.meve.json` file is a UTF-8 encoded JSON document with the following fields:

| Field         | Type     | Required | Description |
|---------------|----------|----------|-------------|
| `meve_version`| String   | Yes      | Specification version (e.g., `"1.0"`) |
| `file_hash`   | String   | Yes      | SHA-256 digest of the certified file (`"SHA-256:<hex>"`) |
| `issuer`      | String   | Optional | Domain or identifier of the issuer |
| `issuer_type` | Enum     | Yes      | `"individual"` or `"professional"` |
| `timestamp`   | String   | Yes      | UTC timestamp in ISO 8601 format |
| `algorithm`   | Enum     | Yes      | `"SHA-256"` (mandatory), `"SHA-512"` (optional future) |
| `signature`   | String   | Yes      | Base64-encoded digital signature |
| `extensions`  | Object   | Optional | Future-proofing for custom fields |

---

## 5. Cryptographic Algorithms

### Hash Functions
- **SHA-256** → mandatory.  
- **SHA-512** → optional, recommended for high-security contexts.  

### Signature Schemes
- **Ed25519** → mandatory (default).  
- **RSA-2048** → optional fallback.  
- **ECDSA (P-256)** → optional, for interoperability.  

---

## 6. Generation Process
1. Compute file hash (`SHA-256`).  
2. Prepare JSON structure with required fields.  
3. Sign concatenated fields with issuer’s private key.  
4. Output `.meve.json` file alongside the original file.  

---

## 7. Verification Process
To validate a file with its `.meve.json` certificate:
1. Compute file hash and compare with `file_hash`.  
2. Validate `signature` using issuer’s public key.  
3. If `issuer` is a domain, check DNS TXT record:

_meve.example.com TXT "pubkey=<base64>"

4. Confirm timestamp is valid (optional external audit).  

---

## 8. Compliance and Security
- **GDPR compliant** → no personal data stored by default.  
- **Transparency** → open format, auditable code.  
- **Durability** → JSON ensures readability in any language.  
- **Threat model** → protects against tampering, forgery, replay attacks.  

---

## 9. Examples

### Individual Certificate
```json
{
  "meve_version": "1.0",
  "file_hash": "SHA-256:78bd6b1ca7fb38c81feefe71...",
  "issuer_type": "individual",
  "timestamp": "2025-09-22T12:00:00Z",
  "algorithm": "SHA-256",
  "signature": "B64-SIGNATURE-EXAMPLE"
}

Professional Certificate with DNS Binding

{
  "meve_version": "1.0",
  "file_hash": "SHA-256:7be1c0ff13e3bc01...",
  "issuer": "digitalmeve.com",
  "issuer_type": "professional",
  "timestamp": "2025-09-22T12:00:00Z",
  "algorithm": "SHA-256",
  "signature": "B64-SIGNATURE-EXAMPLE"
}


---

10. Extensions and Future Work

Multi-signature (several issuers sign the same file).

External timestamping (integration with blockchain or TSA).

Compression (binary .meve format, optional).

Localized metadata (language, region, jurisdiction).



---

11. Compatibility

Backward-compatible by version (meve_version).

Verifiers must ignore unknown fields.

New algorithms/extensions only added via minor version upgrades.



---

12. Governance

Changes to the standard follow:

Public proposals via GitHub (ADR process).

Semantic versioning:

Major = breaking changes.

Minor = new features/extensions.

Patch = clarifications, fixes.




---

13. References

RFC 8032: Edwards-Curve Digital Signature Algorithm (EdDSA)

RFC 6234: SHA-2 Hash Functions

NIST SP 800-57: Key Management



---

End of Document

---
