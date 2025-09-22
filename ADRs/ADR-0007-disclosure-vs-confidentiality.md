# ADR-0007: Disclosure vs. Confidentiality Strategy

## Status  
Accepted — 2025-09-22  

## Context  
DigitalMeve is designed as a **global certification standard**, with ambitions comparable to PDF, SSL/TLS, or DNSSEC.  
For global adoption, **transparency** is critical: developers, enterprises, and regulators must trust the specification.  

However, absolute transparency creates risks:  
- **Security risks** if invisible watermarking, SHA-256 embedding, DigitalMeve invisible keys, or pro patches were entirely disclosed.  
- **Business risks** if differentiating know-how (e.g., enterprise private key generation, invisible patch layers) were trivial to replicate.  

A methodology is required to balance **open standards** (to build trust) and **confidential innovation** (to maintain security and differentiation).

## Decision  
1. **Public Standard (Core .MEVE)**  
   - Open, auditable, documented in this repository.  
   - Covers certificate structure, file binding, hash-based verification, governance, and minimal examples.  
   - Licensed permissively (CC BY 4.0 or Apache 2.0).  
   - Ensures anyone can verify authenticity without depending on closed systems.  

2. **Confidential Layers (DigitalMeve proprietary)**  
   - Invisible watermarking, invisible DigitalMeve key, SHA-256 injection, and enterprise private-key binding are **not fully documented publicly**.  
   - Only high-level principles are disclosed in `SECURITY_MODEL.md` and the Whitepaper.  
   - Full implementation details are reserved for DigitalMeve’s internal team to prevent forgery and to protect customers.  

3. **For Paying Users**  
   - Individuals: certificate includes nominative data (name or email).  
   - Professionals: enterprise private keys issued to sign in the company’s name, with an additional invisible patch reinforcing trust.  
   - Both tiers: visible watermark, invisible SHA-256, and invisible DigitalMeve key embedded in each document.  

4. **For the Ecosystem**  
   - Developers and integrators see the **public spec** and APIs.  
   - Enterprises gain additional confidential documentation under NDA.  
   - Open-source libraries exist for verification, but generation of “Pro patches” remains closed.  

## Consequences  
- Builds **global trust** via openness (verification is public and audit-ready).  
- Maintains **security and uniqueness** via confidential, proprietary embedding mechanisms.  
- Balances **standardization** (like PDF or TLS) with **differentiation** (DigitalMeve invisible protections).  
- Positions DigitalMeve as both a **worldwide open standard** and a **trusted commercial solution**.

---
