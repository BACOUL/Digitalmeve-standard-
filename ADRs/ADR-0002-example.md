# ADR-0002: DigitalMeve Certificate Format

- **Status:** Accepted  
- **Date:** 2025-09-22  
- **Author(s):** DigitalMeve Core Team  
- **Context:** Standardization of proof certificates  

---

## 1. Context

Every DigitalMeve-protected file must be accompanied by a certificate that is **human-readable** and **machine-verifiable**.  
The certificate:

- Provides **evidence of authenticity**  
- Contains **cryptographic proof** (hash digest)  
- Is **independent of the file type**  
- Must be **portable and easy to share** (no special tools required)  

The challenge is to design a format that balances **readability**, **universality**, and **security**.  

---

## 2. Decision

We define the **DigitalMeve Certificate** as an **HTML file (.html)** that includes both **human-readable metadata** and **machine-verifiable JSON data** embedded inside.  

- **File extension:** `.meve.html`  
- **Content:**  
  - Certificate header (branding, timestamp, issuer type)  
  - File metadata (filename, MIME type, size, date of certification)  
  - Cryptographic proof (SHA-256 digest, DigitalMeve reference key)  
  - Issuer details (anonymous / individual / enterprise)  
  - Verification instructions (links to DigitalMeve tools)  
- **Embedded JSON-LD block** for machine parsing.  

---

## 3. Rationale

- **Universal:** HTML can be opened on any device, without special software.  
- **Readable:** Users see all key information clearly (like a PDF invoice).  
- **Verifiable:** Embedded JSON ensures consistent parsing and automation.  
- **Auditable:** Certificates can be archived, printed, or shared without breaking integrity.  

---

## 4. Alternatives Considered

- **JSON only (.json):** Developer-friendly but not user-friendly.  
- **PDF certificate:** Professional look but heavier and less universal.  
- **Blockchain anchoring:** Adds cost/complexity; optional for future.  

Decision: **HTML+JSON hybrid** is the best compromise for global adoption.  

---

## 5. Consequences

- **Positive:**  
  - Certificates can be read by humans and validated by machines.  
  - Portable across platforms, including email attachments and archives.  
  - Scales for individuals (lightweight) and enterprises (integrated).  

- **Negative:**  
  - HTML may be altered if not handled securely (mitigated by signature).  
  - Slightly larger file size than pure JSON.  

---

## 6. Future Work

- Define **DigitalMeve Certificate v2** with optional **enterprise branding** and **visual watermark integration**.  
- Add **multi-language support** inside the certificate.  
- Provide a **CLI tool and SDK** for developers to auto-generate and parse certificates.  

---

## 7. Example

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <title>DigitalMeve Certificate</title>
</head>
<body>
  <h1>DigitalMeve Certificate — VALID ✅</h1>
  <p><strong>File:</strong> Contract-2025.docx</p>
  <p><strong>Certified on:</strong> 2025-09-22 10:32:15 UTC</p>
  <p><strong>SHA-256:</strong> 78bd6b1ca7fb38c81feefe71354ae749297890f8d33731c7c9074e2364ace149</p>
  <p><strong>Issuer:</strong> Individual (Anonymous)</p>
  <p><strong>Standard:</strong> DigitalMeve v1</p>
  <p>Verify at: <a href="https://digitalmeve.com/verify">digitalmeve.com/verify</a></p>

  <!-- Machine-readable block -->
  <script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "DigitalDocument",
    "name": "Contract-2025.docx",
    "sha256": "78bd6b1ca7fb38c81feefe71354ae749297890f8d33731c7c9074e2364ace149",
    "issuer": "Anonymous",
    "issuedOn": "2025-09-22T10:32:15Z",
    "standard": "DigitalMeve v1"
  }
  </script>
</body>
</html>
