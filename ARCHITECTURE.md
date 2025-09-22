# DigitalMeve — Architecture

Invisible proof. Visible trust.  
This document describes the technical architecture of **DigitalMeve**, the global standard for embedding invisible, tamper-proof certificates inside any file format (PDF, DOCX, JPG, PNG, MP4, etc.), with verification that is instant, universal, and private.

---

## 📖 Table of Contents
- [1. Overview](#1-overview)
- [2. Core Principles](#2-core-principles)
- [3. File Processing Pipeline](#3-file-processing-pipeline)
  - [3.1 Proof Embedding](#31-proof-embedding)
  - [3.2 Watermark Layer](#32-watermark-layer)
  - [3.3 Hashing & Keys](#33-hashing--keys)
- [4. Certificate Format](#4-certificate-format)
  - [4.1 HTML Certificate](#41-html-certificate)
  - [4.2 Metadata Fields](#42-metadata-fields)
  - [4.3 Enterprise Extensions](#43-enterprise-extensions)
- [5. Verification Flow](#5-verification-flow)
  - [5.1 Local Verification](#51-local-verification)
  - [5.2 Universal Access](#52-universal-access)
  - [5.3 Failure Cases](#53-failure-cases)
- [6. DNS Binding (Pro/Enterprise)](#6-dns-binding-proenterprise)
- [7. Keys & Signatures](#7-keys--signatures)
  - [7.1 Individual Certificates](#71-individual-certificates)
  - [7.2 Professional Certificates](#72-professional-certificates)
  - [7.3 Enterprise Private Keys](#73-enterprise-private-keys)
- [8. Security Layers](#8-security-layers)
  - [8.1 Visible Proofs](#81-visible-proofs)
  - [8.2 Invisible Proofs](#82-invisible-proofs)
  - [8.3 Multi-layer Verification](#83-multi-layer-verification)
- [9. Scalability & Interoperability](#9-scalability--interoperability)
- [10. Future Extensions](#10-future-extensions)

---

## 1. Overview
DigitalMeve allows any file to contain **three levels of protection**:
1. **Visible watermark** → signals the file is certified.  
2. **Invisible SHA-256 hash** → ensures integrity.  
3. **Invisible DigitalMeve key** → guarantees authenticity across time and formats.  

Verification works instantly, without servers. Certificates are generated in **HTML format** for transparency and long-term accessibility.

---

## 2. Core Principles
- **Privacy-first** → All processing runs locally (browser or SDK).  
- **Universality** → Works with any file type (.pdf, .docx, .jpg, .png, .mp4).  
- **Zero friction** → No account required for free certification.  
- **Open standard** → Documentation, specs, and governance are public.  
- **Enterprise ready** → DNS binding, private keys, and branding.  

---

## 3. File Processing Pipeline

### 3.1 Proof Embedding
When a file is certified:
- The original content remains **unchanged and private**.  
- An **invisible SHA-256 hash** is embedded.  
- An **invisible DigitalMeve key** is inserted for universal verification.  

### 3.2 Watermark Layer
- A **visible watermark** (DigitalMeve seal) is added.  
- For enterprises, an **optional branded watermark** can be used.  

### 3.3 Hashing & Keys
- SHA-256 is used for file fingerprinting.  
- Invisible keys are tied to the certificate, not the file format.  

---

## 4. Certificate Format

### 4.1 HTML Certificate
Each certification generates a companion file:
- The `.meve.html` contains metadata, signature, and validation status.  
- It can be opened in any browser.  

### 4.2 Metadata Fields
Standard fields:
- File name + hash (SHA-256)  
- Timestamp of certification  
- Certificate issuer (individual name/email, or enterprise reference if applicable)  
- DigitalMeve signature  

### 4.3 Enterprise Extensions
- DNS binding (`.well-known/meve.html`)  
- Private enterprise key reference  
- Optional legal statements  

---

## 5. Verification Flow

### 5.1 Local Verification
Users drag & drop a file into the DigitalMeve verifier.  
- The embedded SHA-256 is extracted.  
- The invisible DigitalMeve key is verified.  
- The visible watermark is compared.  

### 5.2 Universal Access
Verification can happen:
- In browser (Web verifier).  
- With CLI / SDK tools.  
- Via enterprise APIs.  

### 5.3 Failure Cases
If a file fails verification:
- Tampered content → mismatch with SHA-256.  
- Invalid signature → fails DigitalMeve key check.  
- Expired/invalid enterprise binding → DNS verification fails.  

---

## 6. DNS Binding (Pro/Enterprise)
- Enterprises can bind their domain name to DigitalMeve certificates.  
- A file certified by `company.com` can be independently verified through DNS records.  
- DNS entries are stored at `https://company.com/.well-known/meve.html`.  

---

## 7. Keys & Signatures

### 7.1 Individual Certificates
- Free tier → anonymous proof only.  
- Paid tier → name/email visible in certificate.  

### 7.2 Professional Certificates
- Includes **named certificate**.  
- Metadata embeds the professional’s reference.  

### 7.3 Enterprise Private Keys
- Each enterprise receives a **private key** for internal signing.  
- Used to issue branded certificates.  
- Enables audit logs and compliance.  

---

## 8. Security Layers

### 8.1 Visible Proofs
- Standard watermark for all files.  
- Optional branded watermark for enterprises.  

### 8.2 Invisible Proofs
- Embedded SHA-256 (integrity).  
- Embedded DigitalMeve key (authenticity).  

### 8.3 Multi-layer Verification
- Local hash validation.  
- Certificate signature validation.  
- DNS binding validation (Pro/Enterprise).  

---

## 9. Scalability & Interoperability
- Works across all formats (PDF, DOCX, JPG, PNG, MP4).  
- Certificates are **HTML-based**, ensuring long-term readability.  
- Architecture designed for **post-quantum cryptography upgrades**.  

---

## 10. Future Extensions
- **Post-quantum algorithms** (Kyber/Dilithium).  
- **Blockchain anchoring** for optional timestamping.  
- **Enterprise dashboards** for bulk certification.  
- **Cross-platform SDKs** (Node.js, Python, Rust).  

---

📌 DigitalMeve architecture is designed to balance **privacy, universality, and enterprise compliance**, while keeping certain implementation details **confidential** for security reasons.
