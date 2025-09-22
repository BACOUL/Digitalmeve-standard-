# DigitalMeve Architecture

**Version:** v1.0 (Draft)  
**Status:** Public Specification  
**License:** CC BY 4.0

This document defines the end-to-end architecture of DigitalMeve: how files are certified and verified, how professional keys and DNS binding work, and how the HTML certificate is structured. It is intended for developers, auditors, and enterprises. Proprietary details of invisible embeddings (how the SHA-256 and the DigitalMeve tag are physically inserted into files) are intentionally confidential and NOT disclosed here; this document specifies only the public contract and verifier behavior.

## 1. Purpose & Scope

- Provide a universal, privacy-first method to **certify** and **verify** any digital file.
- Guarantee **integrity** (SHA-256), **authenticity** (signatures for Pro), and **durability** (human- and machine-readable certificate).
- Keep all core operations **on-device** (no upload).
- Support **Individuals** (free and paid) and **Professionals** (Pro/Enterprise).
- Maintain a clear separation between **public standard** and **confidential implementations** of on-file protections.

## 2. Design Goals & Constraints

- **On-device first**: hashing, embedding, signing, and verification run locally.
- **Universal**: works for PDF, DOCX, PNG/JPG, ZIP, TXT, MP4, and more.
- **Open verification**: anyone can verify with public tools; no hidden servers required.
- **Future-proof**: stable HTML certificate + JSON machine block; DNS binding for organizational trust.
- **No encryption in core**: confidentiality is out of scope; the core is proof of integrity/authenticity.

## 3. Core Concepts

- **Visible watermark**: a small, human-readable “DigitalMeve Certified” mark; for Pro, may include organization name or reference.  
- **Invisible SHA-256**: the file’s SHA-256 digest is embedded invisibly.  
- **Invisible DigitalMeve tag (MEVE patch)**: proprietary marker improving tamper resistance.  
- **Certificate (HTML)**: a sidecar file (default) `filename.ext.meve.html` containing both a human view and a machine-readable JSON block used by verifiers.  
- **Issuer types**: `individual` (anonymous for free; name/email for paid) and `professional` (domain-bound, signed).  
- **KID**: key identifier for Pro signatures and rotation.  
- **Verification levels**: L0 (watermark), L1 (hash), L2 (Pro signature + DNS), L3 (enhanced on-file protections).

## 4. System Components

- **Client App (Web/UI/CLI)**: performs hashing, applies visible and invisible protections, builds the certificate HTML, and (for Pro) signs locally.
- **Public Verifier**: parses the certificate HTML, recomputes the hash, optionally resolves DNS/`.well-known`, and reports verdict.
- **DNS /.well-known**: public discovery of Pro public keys and rotation windows.
- **(Optional) Enterprise APIs**: batch certification and verification endpoints (hash-based), never uploading file contents.

## 5. Certification Flow (Generate)

### 5.1 Inputs
- Local file (`file.ext`), any supported type.
- Issuer context:
  - **Individual (Free)**: anonymous (no issuer identity).
  - **Individual (Paid)**: issuer name or email included in certificate.
  - **Professional**: domain + private key (ed25519 recommended), `kid`, optional display name.

### 5.2 Steps (all on-device)
1. **Pre-validation**: mime/type/size checks.
2. **Hash**: compute `SHA-256(file_bytes)` → lowercase hex.
3. **On-file protections**:
   - Apply **visible watermark** (file-type dependent).
   - Embed **invisible SHA-256**.
   - Embed **invisible DigitalMeve tag**.
   - Note: exact embedding algorithms are confidential; the public contract only requires that these protections be present.
4. **Certificate build**:
   - Prepare machine JSON block with: version, file name, mime, sha256, algorithm, timestamp (UTC ISO-8601), issuer_type, issuer (if any), issuer_display_name (Pro), `kid` (Pro), `sig_alg` (Pro).
   - For **Professionals**: build canonical signing input (see §9) and sign with the issuer private key; attach signature to the machine block.
5. **Certificate HTML**:
   - Render human-readable view (issuer, file, hash, timestamp, call-to-verify).
   - Embed machine block in `<script type="application/meve+json">...</script>`.
6. **Outputs**:
   - **Certified file**: same extension as input, now carrying visible and invisible protections.
   - **Certificate**: `file.ext.meve.html` sidecar (default). Embedding certificate inside the file is possible for some formats but sidecar is the reference method.

## 6. Verification Flow (Verify)

### 6.1 Inputs
- A file alone, or  
- A file plus its sidecar certificate `file.ext.meve.html`.

### 6.2 Steps (all on-device)
1. **Certificate discovery**:
   - If sidecar is provided, parse it.
   - If only the file is provided and supports embedded certificate, extract it; otherwise prompt for the sidecar.
2. **Parse machine block**: read the JSON from `<script type="application/meve+json">`.
3. **Hash check (L1)**: recompute SHA-256 over the provided file bytes and compare to the machine block’s `file_hash`.
4. **Signature check (L2, Pro only)**:
   - If `issuer_type=professional`, resolve public key using DNS TXT or `/.well-known/meve.json` (see §10).
   - Rebuild canonical signing input (see §9) and verify signature with the discovered public key.
5. **On-file protections (L3, optional)**:
   - If the verifier supports proprietary checks, evaluate presence/consistency of invisible protections; otherwise ignore.
6. **Verdict**:
   - `VALID` → all mandatory checks pass (L1 always; L2 for Pro).
   - `INVALID` → hash mismatch, invalid signature, or inconsistent issuer context.
   - `UNKNOWN` → missing certificate/sidecar or unable to resolve Pro keys.
   - Return level `L0|L1|L2|L3`, reasons, and details (issuer, kid, ts, algs).

## 7. File Type Bindings

DigitalMeve supports a broad set of formats. The contract is uniform; embeddings differ internally per format.

- **PDF / DOCX**: visible watermark (page overlay or header/footer), invisible hash/tag in metadata/custom properties.  
- **Images (PNG, JPG, TIFF)**: visible watermark overlay (optional), invisible metadata blocks and/or steganographic carriers.  
- **Other (ZIP, TXT, MP4, binaries)**: invisible metadata blocks where available; otherwise rely on sidecar certificate binding by filename.

**Confidentiality note**: the exact embedding carriers, redundancy, and robustness parameters (e.g., resistance to recompression, cropping, resampling) are proprietary and not disclosed publicly.

## 8. Certificate (HTML) Structure

A DigitalMeve certificate is a self-contained HTML file with a human section and a machine section.

### 8.1 Human section (example)
- Title, logo, “DigitalMeve Certificate”.
- File name, mime type, SHA-256 (shortened for display), timestamp.
- Issuer display:
  - Individual (free): “Anonymous”.
  - Individual (paid): “Issued by: <Name/Email>”.
  - Professional: “Issued by: <Organization>”.
- Call to action: “Verify now”.

## 8.2 Enterprise Extensions

Enterprises may require additional layers of trust, audit, and integration. DigitalMeve supports these extensions:

- **Private Key Integration**: Enterprises receive a dedicated private key pair. Documents can be signed under their corporate identity.
- **DNS Binding**: A DNS TXT record at `_meve.company.com` binds the enterprise certificate root to the company domain.
- **Visible Watermark**: Every enterprise-certified document may include an optional visible watermark (company logo or reference code).
- **Custom Metadata**: Enterprises can attach business metadata (invoice ID, project code, audit number) directly into the .MEVE certificate.
- **Batch Processing**: Large-scale certification pipelines (e.g. 10k+ documents per day) supported via offline/bulk APIs.
- **Compliance Mode**: Optionally log hash references into a compliance ledger (external or self-hosted).

These extensions remain interoperable: any DigitalMeve verification client can still verify enterprise documents, even without the extra metadata.

---

## 9. File Types & Embedding Strategy

DigitalMeve supports both binary and textual formats.

- **PDF**: SHA-256 digest is calculated on the full file. A visible watermark is embedded in a reserved region. The invisible `.MEVE` marker is appended in an unused metadata section.
- **DOCX**: Certificate data injected as a custom XML part; invisible SHA-256 anchor embedded in document properties.
- **Images (PNG/JPG)**: Invisible steganographic marker inserted (subtle, non-destructive). SHA-256 stored in metadata.
- **ZIP**: Entire archive hashed. A `.meve.json` sidecar can be added inside.
- **Generic binary**: Pure certificate file (`.meve.json`) accompanies the binary.

---

## 10. Verification Flow

Verification clients must support:

1. **File Input**  
   User drags & drops the file into the verifier (browser or CLI).
2. **Hash Extraction**  
   - Compute SHA-256 of the full binary.  
   - Extract embedded invisible `.MEVE` marker.  
   - (If enterprise mode) Verify DNS TXT binding and corporate signature.
3. **Certificate Lookup**  
   Certificate is embedded in the file itself (no central lookup).  
   Verifier validates JSON schema.
4. **Validation Steps**  
   - Compare recomputed SHA-256 with certificate.  
   - Check timestamp validity (ISO 8601, UTC).  
   - Verify signature (if present).  
   - Report result: ✅ valid / ❌ invalid.
5. **Result Presentation**  
   Display certificate in a human-readable HTML format:  
   - File name  
   - Date, time  
   - Issuer (anonymous, individual, or enterprise)  
   - SHA-256 (truncated + full)  
   - Valid/invalid badge

---

## 11. Cryptographic Considerations

- **Hashing Algorithm**: SHA-256 (NIST standard, collision resistant).  
- **Signatures**: Ed25519 recommended (fast, strong, open).  
- **Timestamp**: Generated client-side; can be anchored in enterprise mode.  
- **Randomness**: Nonces used when embedding invisible watermarks to prevent pattern attacks.  
- **Forward Compatibility**: Hash algorithm is versioned (MEVE v1: SHA-256; MEVE v2: SHA-3, etc.).  
- **Key Management**: Enterprises receive private keys securely (via HSM or PKCS#12 bundle). DigitalMeve does not store keys.

---

## 12. Threat Model

- **Adversary Goal**: Forge a DigitalMeve certificate for a file they did not create.  
- **Mitigations**:  
  - SHA-256 prevents preimage/collision forgery.  
  - Invisible watermark ensures tampering detection.  
  - Enterprise private keys prevent impersonation.  
  - No central DB eliminates “single server” compromise.  

- **Residual Risks**:  
  - If enterprise private key is leaked, adversary may forge under that identity. Mitigation: rotate keys, revoke via DNS.  
  - If file formats are exotic, invisible embedding may fail. Mitigation: fall back to `.meve.json` sidecar.  

---

## 13. Privacy Guarantees

- Files never leave the client device.  
- No uploads, no remote logs.  
- Certificates themselves contain only non-sensitive metadata (hashes, timestamps, optional issuer).  
- Enterprise mode may add identifying metadata, but this is under the enterprise’s control.  
- Verification can be done fully offline.

---

## 14. Governance

- **Specification Ownership**: DigitalMeve Standard is open.  
- **Changes**: Proposed via ADRs (Architecture Decision Records).  
- **Versioning**: Semantic Versioning (SemVer).  
- **Consensus**: Major changes require review and approval.  
- **Interoperability**: Implementations must pass conformance tests.

---

## 15. Roadmap

- **v1.0 (Current)**:  
  - SHA-256 + invisible marker  
  - Visible watermark for PDFs/images  
  - Certificate JSON structure  
  - Browser + CLI reference implementations

- **v1.1 (Planned)**:  
  - Enterprise private key support  
  - DNS binding  
  - Batch certification API

- **v2.0 (Future)**:  
  - Alternative hash algorithms (SHA-3, BLAKE3)  
  - Ledger anchoring (optional)  
  - Rich metadata profiles

---

## 16. Example Certificate (HTML)

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>DigitalMeve Certificate</title>
    <style>
      body { font-family: sans-serif; background: white; color: black; }
      .valid { color: green; font-weight: bold; }
      .invalid { color: red; font-weight: bold; }
    </style>
  </head>
  <body>
    <h1>DigitalMeve Certificate — VALID ✅</h1>
    <p><strong>File:</strong> invoice-2025Q1.pdf</p>
    <p><strong>Date:</strong> 2025-09-18</p>
    <p><strong>Time:</strong>00:46:34 UTC</p>
    <p><strong>Issuer:</strong> Example Corp (via DNS binding)</p>
    <p><strong>SHA-256:</strong> 78bd6b1c...e2364ace149</p>
    <p><strong>MEVE Version:</strong> 1</p>
  </body>
</html>
## 17. Appendix

### 17.1 File Extensions
- **`.meve.json`** — Detached certificate (sidecar) for any file type.
- **`.pdf` / `.docx` / `.jpg` / `.png`** — Native embedding of watermark + invisible marker.
- **`.zip`** — Archive certification with embedded `.meve.json`.

### 17.2 Terminology
- **Invisible Marker**: Cryptographic anchor (SHA-256 hash + Meve code) embedded in the file metadata or unused structure, undetectable by normal viewers.  
- **Visible Watermark**: Human-visible overlay (e.g., “DigitalMeve Certified” or company logo) displayed on the file for transparency.  
- **Certificate**: A `.meve.json` (machine-readable) or `.html` (human-readable) proof of authenticity bound to the file.  
- **Issuer**: Entity that created the certificate (anonymous, individual, or enterprise).  
- **Enterprise Key**: Private key issued to professional customers, allowing signing on behalf of a company domain.  

### 17.3 Open Source Reference
- **GitHub Repository**: Official reference implementations, examples, and conformance tests are available.  
- **Sample Files**: Test PDFs, DOCX, and images provided with pre-certified examples.  
- **CLI Tools**: Basic `generate` and `verify` commands for developers.  
- **Browser Verifier**: Web-based drag-and-drop tool for end users.  

### 17.4 Contact & Governance
- **Contact**: info@digitalmeve.com  
- **Governance Model**:  
  - Open contribution via GitHub pull requests and ADRs.  
  - Semantic versioning (SemVer) for all spec updates.  
  - Community review required for breaking changes.  

### 17.5 Compliance Notes
- **GDPR / Privacy**: Files never leave the user’s device; no central server logs are required.  
- **Auditability**: All enterprise extensions (DNS, private keys, visible watermarks) remain backward-compatible with the open verifier.  
- **Longevity**: Certificates are designed to remain valid across decades, file formats, and software ecosystems.  

---

🔒 This appendix is the authoritative reference for implementers, partners, and auditors.
