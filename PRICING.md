# DigitalMeve Pricing Model

DigitalMeve follows a **transparent, global pricing model** designed for both individuals and professionals.  
All subscriptions include core certification features, with additional value layers for paying users.

---

## 1. Free Plan (Entry / Trial)

- **Limit:** 5 certifications per month  
- **Certificate:** Anonymous, browser-only  
- **Watermark:** Visible SHA-256 watermark  
- **Invisible markers:** Embedded DigitalMeve signature (basic level)  
- **Support:** Community support only  
- **Audience:** Students, casual creators, testers  

---

## 2. Individual Plan

- **Price:** €9.90/month or €99/year (billed annually)  
- **Limit:** Unlimited certifications  
- **Certificate personalization:** Name or email of certifier embedded in certificate  
- **Markers:**  
  - Visible watermark (SHA-256)  
  - Invisible DigitalMeve signature  
- **Support:** Priority support  
- **Audience:** Freelancers, creators, professionals needing personal certification  

---

## 3. Professional Plan

- **Price:** €29.90/month or €299/year (billed annually)  
- **Limit:** Unlimited certifications  
- **Enterprise-grade features:**  
  - Private key issued for enterprise signing  
  - Certificates tied to company identity (DNS binding, name displayed)  
  - Invisible DigitalMeve enterprise patch  
  - SHA-256 visible watermark  
- **Support:** Premium support with SLA  
- **Audience:** Agencies, law firms, studios, SMEs  

---

## 4. Enterprise (Custom)

- **Price:** Custom pricing (volume licensing)  
- **Features:**  
  - Bulk certification API  
  - Dedicated DNS integrations  
  - Audit-ready reporting  
  - Multi-user management  
  - Advanced governance features  
- **Audience:** Large companies, governments, certification bodies  

---

## 5. Billing & Payment

- All payments processed via **Stripe** (PCI-DSS compliant).  
- Accepted payment methods: credit card, debit card, SEPA, localized wallets (Apple Pay, Google Pay, etc.).  
- Subscriptions auto-renew monthly or yearly.  

---

## 6. Refund Policy

- 14-day refund guarantee for annual subscriptions (EU consumer directive compliant).  
- No refunds for monthly subscriptions once a billing cycle has started.  
- Exceptions granted for technical issues or double charges.  

---

## 7. Compliance

- DigitalMeve follows international pricing and refund regulations:  
  - **EU Consumer Rights Directive** (14-day withdrawal for annual plans).  
  - **Stripe compliance** for payment security.  
  - **Localized tax rules** (VAT, GST, sales tax automatically applied).  

---

## 8. Localized Pricing

- Base prices: €9.90 (Individual), €29.90 (Professional).  
- Prices automatically **localized by Stripe**:  
  - Currency conversion updated in real time.  
  - Regional taxes applied automatically.  
  - Optional purchasing power parity adjustments (regional pricing tiers).  

### Example (illustrative)

| Country        | Individual | Professional |
|----------------|------------|---------------|
| France (EUR)   | €9.90      | €29.90        |
| USA (USD)      | $9.90      | $29.90        |
| UK (GBP)       | £8.90      | £26.90        |
| India (INR)    | ₹499       | ₹1499         |

### Implementation

- Stripe Checkout detects user location.  
- Shows local currency and applies tax.  
- Admin configures regional tiers in Stripe dashboard.  

---

## 9. Summary

- **Free Plan:** 5 certifications/month, anonymous.  
- **Individual Plan:** €9.90/month, personal name/email in certificate.  
- **Professional Plan:** €29.90/month, enterprise-grade private key + DNS.  
- **Enterprise:** Custom pricing, bulk API, advanced governance.  

DigitalMeve ensures **fair, transparent, and compliant global pricing** — aligned with international standards for SaaS and digital certification.
