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

### 8.2 Machine section (mandatory)
Embed one `<script type="application/meve+json">` with minimally:

```json
{
  "version": "1.0",
  "file_name": "invoice.pdf",
  "mime_type": "application/pdf",
  "file_hash": "78bd6b1ca7fb38c81feefe71354ae749297890f8d33731c7c9074e2364ace149",
  "algorithm": "SHA-256",
  "timestamp": "2025-09-22T14:12:00Z",
  "issuer_type": "professional",
  "issuer": "acme.example",
  "issuer_display_name": "ACME Inc.",
  "kid": "2025-q3",
  "sig_alg": "ed25519",
  "signature": "BASE64URL_SIGNATURE"
}
