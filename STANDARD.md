# STANDARD.md — The .MEVE Standard (DigitalMeve)

Version: 1.0.0  
Date: 2025-09-22  
Status: Draft — Public specification with confidential implementation details redacted.

## Table of contents

1. Introduction  
2. Terminology & Conventions  
3. Scope & Goals  
4. File extensions & distribution model  
5. Certificate structure (public schema)  
6. Proof model (high level)  
7. Generation flow (normative, abstract)  
8. Verification flow (normative)  
9. Error codes & responses  
10. Privacy & data minimization  
11. Interoperability & formats  
12. Versioning & backwards compatibility  
13. Security-sensitive elements (redacted)  
14. Partner onboarding & NDA access  
15. Appendix: JSON schemas & examples (public parts)  
16. Change log

---

## 1. Introduction

This document defines the **.MEVE** certificate standard — a privacy-first, portable, verifiable certificate format for arbitrary digital files.  
.digitalmeve aims to provide tamper-evident proofs combining a visible marker (watermark) and cryptographic fingerprints so that any recipient can verify authenticity **without requiring file upload**.

This spec separates **public, auditable primitives** from **implementation secrets**. Public primitives (hashing, signatures) are fully specified; implementation details that would weaken security if public (exact embedding algorithm for the invisible marker, secret key handling, proprietary patch formats) are intentionally redacted.

---

## 2. Terminology & Conventions

- **Document / File** — any binary asset (PDF, DOCX, PNG, JPG, MP4, ZIP, …).  
- **Certificate** — `.meve` artifact (see §5) representing proof about a file. Typically delivered as a standalone HTML certificate and optionally as a companion file wrapper.  
- **Issuer** — the entity (anonymous / individual / professional / enterprise) that created the certificate.  
- **SHA-256** — the hashing algorithm used for public fingerprinting.  
- **DigitalMeve Proof** — a multi-layer proof consisting of a visible watermark and invisible anchors (high-level in §6).  
- **Verify** — the operation that confirms if a file matches its certificate and whether the proof remains valid.

Conventions: normative keywords follow RFC style — MUST, SHOULD, MAY, RECOMMENDED.

---

## 3. Scope & Goals

The .MEVE standard is designed to:

- Provide **portable**, human- and machine-readable certificates.  
- Ensure **privacy**: files are processed client-side; no file storage is required.  
- Be **format-agnostic**: support for any binary type.  
- Allow **enterprise identity** via DNS binding and enterprise keys.  
- Be **auditable**: public JSON schemas for certificate metadata.

This standard does **not** define legal frameworks; it provides technical artifacts that can be used as evidence per local law.

---

## 4. File extensions & distribution model

- Primary certificate artifact: `certificate.meve.html` (human-readable + embedded JSON metadata).  
- Optional wrapped file formats (examples):  
  - `originalfilename.pdf.meve.pdf` — PDF wrapper approach (non-invasive).  
  - `originalfilename.jpg.meve.jpg` — image wrapper.  
  - `originalfilename.bin.meve` — generic binary wrapper.  

Implementations MAY choose to embed or attach certificates. The canonical representation for interchange is the standalone `.meve.html` certificate accompanied by the original file (not stored by the service).

---

## 5. Certificate structure (public schema)

A certificate is a JSON object embedded inside an HTML container. The **public** fields are:

```json
{
  "meve_version": "1",
  "certificate_id": "string (UUIDv4)",
  "issued_at": "ISO8601 timestamp UTC",
  "file": {
    "filename": "string",
    "sha256": "hex string",
    "size": "integer bytes",
    "mime": "string"
  },
  "issuer": {
    "type": "anonymous | individual | professional | enterprise",
    "name": "string (optional for paid individuals/professionals)",
    "identifier": "string (email or DID or domain, optional)"
  },
  "anchors": [
    {
      "type": "sha256",
      "value": "hex string"
    },
    {
      "type": "digitalmeve:visible_watermark",
      "value": "human-readable label"
    }
    /* other public anchors */
  ],
  "signatures": [
    {
      "algorithm": "string (e.g., ECDSA-P256-SHA256)",
      "key_id": "string (public key identifier)",
      "signature": "base64"
    }
  ],
  "metadata": {
    "meve_tool_version": "string",
    "additional": {}
  }
}
Normative: `meve_version`, `certificate_id`, `issued_at`, and `file.sha256` MUST be present. `signatures` MUST include at least one signature when issuer type is `professional` or `enterprise`.

---

## 6. Proof model (high level)

The .MEVE proof is **multi-layered**:

- **Layer 1 — SHA-256 fingerprint**: public, canonical hash of the canonicalized file bytes. This fingerprint is the primary proof of integrity.
- **Layer 2 — Visible watermark**: a human-readable mark integrated in the document (for deterrence and traceability).
- **Layer 3 — Invisible anchors**: embedded cryptographic markers (.MEVE invisible code) linked to the file structure but not altering its visible rendering.
- **Layer 4 — Issuer identity**: for paid individuals and professionals, the issuer’s name/email or DNS identifier is embedded.
- **Layer 5 — Signature**: for professional/enterprise tiers, the certificate is signed with a private key unique to the entity.

---

## 7. File integration

- **Visible watermark**: MUST be unobtrusive but legible (e.g., small text in footer or corner).
- **Invisible SHA-256**: MUST be embedded in the file’s binary structure or metadata in a way that does not alter user experience.
- **Invisible DigitalMeve anchor**: a unique identifier injected in metadata for redundancy and detection of tampering.
- **Professional patch**: optional additional invisible markers for enterprise-grade protection.

---

## 8. Verification process

1. User drops a file + its .MEVE certificate into the verifier tool.
2. Tool re-computes SHA-256 fingerprint of the file.
3. Tool checks that the fingerprint matches the one inside the certificate.
4. Tool validates presence of invisible anchors and visible watermark.
5. Tool checks signature if present:
   - For professionals/enterprises: verifies ECDSA signature against the known public key (DNS-bound or registry).
6. Tool displays result: **VALID**, **TAMPERED**, or **INVALID**.

Normative: Verification MUST be fully client-side and MUST NOT require a network call (except optional DNS resolution for pro issuers).

---

## 9. Professional and enterprise extensions

- **Private keys**: Each pro/enterprise issuer receives a private key bound to their domain (DNS TXT record or DID).  
- **DNS binding**: Public keys are published under a `.well-known/meve.json` file or DNS TXT entry.  
- **Custom watermarking**: Enterprises MAY configure visible watermark templates.  
- **Audit trail**: Enterprises MAY maintain an internal ledger of certificates issued, but the standard itself remains stateless.  

---

## 10. Individual (paid) extensions

- Paid individual certificates MUST include the name or email of the issuer in the `issuer` object.  
- Such fields MUST be visible in the certificate but MAY be anonymized in the visible watermark (configurable).  

---

## 11. Canonicalization rules

- Line endings MUST be normalized to LF (`\n`) before hashing.  
- Files MUST be hashed as raw bytes with no additional transformations.  
- Metadata fields (issuer name, etc.) MUST NOT affect the file hash, only the certificate.  

---

## 12. File formats

- Any file type is supported (binary, text, image, PDF, DOCX, etc.).  
- For structured formats (PDF, DOCX), invisible anchors SHOULD be embedded in metadata sections.  
- For images, anchors MAY be steganographically embedded (implementation detail, not normative).  

---

## 13. Trust anchors

- **Root trust**: SHA-256 fingerprint + visible watermark.  
- **Intermediate trust**: invisible DigitalMeve anchor.  
- **Organizational trust**: professional/enterprise private keys + DNS.  

---

## 14. Error states

- **MISMATCH**: file hash ≠ certificate.  
- **MISSING_ANCHOR**: invisible code not found.  
- **INVALID_SIGNATURE**: pro/enterprise signature cannot be verified.  
- **EXPIRED**: (reserved for future, if certificates carry validity).  

---

## 15. Backward compatibility

- `.MEVE` v1 MUST always be verifiable with the v1 spec.  
- Future versions MUST increment `meve_version` field and preserve ability to verify older certificates.  

---

## 16. Change log

- v1.0 — Initial release (SHA-256, watermark, invisible anchors, DNS binding, signatures).  
- v1.1 — (Reserved).  
- v2.0 — (Planned: multi-hash, PQ crypto, ledger integration).
