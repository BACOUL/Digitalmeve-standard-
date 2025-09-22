# ADR-0001: Hashing Standard for DigitalMeve Certificates

- **Status:** Accepted  
- **Date:** 2025-09-22  
- **Author(s):** DigitalMeve Core Team  
- **Context:** Global standardization effort  

---

## 1. Context

DigitalMeve requires a reliable and universally trusted hashing mechanism to ensure that every certified file can be uniquely identified, verified, and protected against tampering.  
The hashing algorithm must be:

- **Widely adopted** in industry and academia  
- **Cryptographically strong** (collision- and preimage-resistant)  
- **Regulatory compliant** (used in banking, legal, government systems)  
- **Future-proof** with clear upgrade paths  

---

## 2. Decision

We adopt **SHA-256** (part of the SHA-2 family) as the **primary hashing algorithm** for all DigitalMeve certificates.

- Each file certified with DigitalMeve will be hashed locally on the user’s device.  
- The resulting SHA-256 digest will be embedded in the certificate (HTML format).  
- Verification processes will recompute the SHA-256 of the provided file and compare it to the digest stored in the certificate.  

---

## 3. Rationale

- **Trust & Standardization:** SHA-256 is an international standard (FIPS 180-4, ISO/IEC 10118-3).  
- **Adoption:** Used in TLS, Bitcoin, blockchain protocols, PKI systems.  
- **Performance:** Efficient in modern browsers, optimized across devices.  
- **Security:** No practical collisions known, strong resistance to attacks.  
- **Compliance:** Accepted under GDPR, eIDAS, NIST, and similar regulations worldwide.  

---

## 4. Alternatives Considered

- **SHA-1:** Deprecated due to collisions, not acceptable.  
- **MD5:** Deprecated, insecure, not acceptable.  
- **SHA-3 (Keccak):** Secure but less widely adopted; may be introduced later as optional.  
- **BLAKE3:** Extremely fast but lacks long-term regulatory approval.  

Decision: **Stay with SHA-256** for stability and regulatory acceptance, with an **open upgrade path** to SHA-3 or other modern algorithms if required.  

---

## 5. Consequences

- **Positive:**  
  - Universal compatibility and acceptance.  
  - Developers can implement verification with standard libraries.  
  - Long-term trust in the integrity of certificates.  

- **Negative:**  
  - Larger digest size (256 bits) compared to older algorithms.  
  - Performance is lower than BLAKE3 for very large files, but acceptable for DigitalMeve’s scope.  

---

## 6. Future Work

- Monitor cryptographic research and standards for SHA-256 deprecation.  
- Evaluate SHA-3 and BLAKE3 as potential future additions.  
- Establish versioning in certificates to allow seamless algorithm migration.  

---

## 7. References

- NIST FIPS 180-4: Secure Hash Standard  
- ISO/IEC 10118-3:2004 – Hash Functions  
- [RFC 6234: US Secure Hash Algorithms (SHA and SHA-based HMAC and HKDF)](https://datatracker.ietf.org/doc/html/rfc6234)  
- Bitcoin Core documentation: Proof-of-work with SHA-256  

---

**Decision:**  
DigitalMeve certificates MUST use **SHA-256** as the default hashing algorithm for file integrity until future ADRs specify otherwise.
