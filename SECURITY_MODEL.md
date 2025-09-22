# Security Model

DigitalMeve protects files through a layered model of **visible and invisible proofs**.  
This document defines the security guarantees, cryptographic primitives, and trust boundaries of the `.MEVE` standard.

---

## 1. Threat Model

DigitalMeve assumes an open and adversarial environment:

- Attackers may intercept, copy, or attempt to forge certified files.  
- Attackers may try to tamper with metadata, certificates, or checksums.  
- Attackers may attempt to impersonate legitimate issuers.  

Out of scope:  
- Physical theft of private keys by negligence.  
- Malicious behavior from a fully trusted issuer (collusion).  
- User devices already compromised by malware at certification time.

---

## 2. Security Layers

Every file certified with DigitalMeve contains **three complementary layers of protection**:

### 2.1 Visible watermark
- Each certified file embeds a visible watermark (“DigitalMeve”) on render.  
- This ensures human recognition of certification.  
- For professional accounts, the watermark may include the company name or reference.  
- Watermarking is resilient but not designed as the primary proof — it is a **deterrent and a visible marker**.

### 2.2 Invisible SHA-256 fingerprint
- Every file is hashed locally with **SHA-256**.  
- The digest is invisibly embedded inside the file, in a location that does not alter its functionality or readability.  
- This fingerprint ensures **bit-level integrity**: any modification produces a different hash and invalidates the certificate.  
- Verifiers recompute the SHA-256 and compare against the embedded value.

### 2.3 DigitalMeve invisible key
- Each file also contains a **DigitalMeve invisible key** — a unique marker proving the file was generated with the DigitalMeve standard.  
- This prevents “look-alike” or fake certificates created by third parties.  
- For individuals (paid plans), the issuer’s name or email is recorded in the certificate metadata (HTML-based).  
- For professionals, a **private key pair** is issued. Files are signed with the private key, enabling client/partner verification against the public key (DNS or `.well-known/meve.json` binding).

---

## 3. Certificate (HTML)

Certificates are exported as lightweight HTML documents:  
- Human-readable layout (issuer, date, file hash, algorithm).  
- Machine-readable embedded JSON block for interoperability.  
- Verifiable in any modern browser without external dependencies.  

---

## 4. Professional Keys

- Each Pro account receives a **unique private key**.  
- Certification embeds the signature alongside the file hash and metadata.  
- Verification is done by resolving the issuer’s DNS or retrieving the public key via `.well-known/meve.json`.  
- This guarantees that **documents truly originate from the stated business**.

---

## 5. Data Handling

- **On-device only**: no file is uploaded to DigitalMeve servers.  
- The system only produces fingerprints, metadata, and certificates.  
- This ensures compliance with **privacy-by-design** and GDPR.

---

## 6. Security Guarantees

- **Integrity**: SHA-256 detects any modification.  
- **Authenticity**: DigitalMeve key + Pro private key binding prevents forgery.  
- **Transparency**: Certificates are auditable HTML with embedded JSON.  
- **Privacy**: Files never leave the device.  
- **Longevity**: Based on open algorithms and simple data structures.

---

## 7. Residual Risks

- A fully compromised endpoint at certification time may produce a false proof.  
- Visible watermarks may be removed by heavy editing, but invisible layers remain verifiable.  
- Private key misuse by professionals remains the responsibility of the key holder.  

---

## 8. Conclusion

DigitalMeve’s layered security — watermark, SHA-256 fingerprint, and invisible DigitalMeve key — provides **global, future-proof proof of authenticity**.  
Professionals gain cryptographic signatures bound to their DNS identity, while individuals benefit from lightweight, anonymous certification.  

The model balances **simplicity, privacy, and cryptographic rigor** to enable DigitalMeve as the **universal certification standard**.
