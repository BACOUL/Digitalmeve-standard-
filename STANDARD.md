# DigitalMeve Standard (v1.0.0)

**La preuve invisible. La confiance visible.**  
DigitalMeve définit un **standard mondial de certification de documents** :  
chaque fichier (PDF, DOC, PNG, …) peut être certifié, vérifié, et partagé sans perte de confiance.

---

## 1. Principles

- **Universal** : works with any file type (text, image, audio, video).  
- **Transparent** : verification is independent, no hidden servers.  
- **Durable** : certificates remain valid across time and formats.  
- **Privacy-first** : files never leave the user’s device.  
- **Scalable** : suitable for individuals, enterprises, and institutions.

---

## 2. Certified File Structure

Every file certified by DigitalMeve contains:

1. **Visible watermark**  
   - A small, human-readable tag:  
     `DigitalMeve Certified – ID#<short-hash>`  
   - Placed in a non-intrusive but permanent way.  
   - Protects against trivial copy or screenshot fraud.

2. **Invisible SHA-256**  
   - Embedded into the file’s metadata or hidden layer.  
   - Ensures integrity: any modification breaks the proof.  
   - Value: `sha256(<original_file>)`.

3. **Invisible DigitalMeve marker (MEVE Patch)**  
   - Proprietary, tamper-resistant hidden signature.  
   - Resistant to format conversions (e.g. PDF → JPG).  
   - ⚠️ **Exact embedding method is confidential.**

---

## 3. Certificate Format

Each certified file comes with a **certificate in HTML format**:  

Example filename: `contract.meve.html`

### Contents:
- **Header**
  - DigitalMeve logo + version.
  - Certificate ID.
- **File Metadata**
  - Original filename.
  - File type.
  - SHA-256 hash.
- **Proof Data**
  - Timestamp (ISO 8601).
  - Unique DigitalMeve signature.
  - Reference watermark code.
- **Certificate Holder**
  - Free plan: anonymous.  
  - Paid individual: includes *name* or *email*.  
  - Pro / Enterprise: includes *company name* + *unique enterprise key*.  
- **Verification**
  - “Verify now” button linking to `/verify`.

---

## 4. Verification Process

1. User uploads file → SHA-256 is recomputed.  
2. Invisible marker (MEVE patch) is checked.  
3. Certificate HTML is parsed:
   - Hash match? ✅  
   - Signature valid? ✅  
   - Certificate holder present (if applicable)? ✅  
4. Result is displayed instantly:
   - ✅ Verified (green)  
   - ⚠️ Mismatch (yellow, tampered file)  
   - ❌ Invalid (red)

Verification is **client-side**, no server dependency.

---

## 5. Keys & Identity

- **Free users** : anonymous certification (filigrane + proof only).  
- **Individuals (paid)** : name/email added in certificate.  
- **Professionals (paid)** :  
  - Dedicated **private key** generated.  
  - Used to sign files and certificates.  
  - Identity bound to company (SIRET/ID).  

---

## 6. Security Model

- Cryptography: SHA-256 + asymmetric signing (Elliptic Curve).  
- Privacy: all proofs generated locally in the browser.  
- Transparency: certificates are plain HTML, auditable by anyone.  
- Resilience: verification does not rely on vendor lock-in.

⚠️ **Details of invisible embedding algorithms are not publicly disclosed.**

---

## 7. File Types Supported

- PDF, DOC/DOCX, XLSX, PNG, JPG, MP4, TXT.  
- Other formats can be supported via **generic binary mode**.

---

## 8. Versioning

- `v1.0.0` → current release (core proof model).  
- `v1.1.0` → enterprise key system.  
- `v2.0.0` → interoperability with public ledgers (optional).

---

## 9. Licensing

Documentation: **CC BY 4.0**  
Certificates & implementations: **proprietary** DigitalMeve core.

---

## 10. Governance

All changes to this standard follow:  
- **ADRs** (Architecture Decision Records).  
- Semantic versioning (`MAJOR.MINOR.PATCH`).  
- Public discussion via GitHub Issues / Pull Requests.
