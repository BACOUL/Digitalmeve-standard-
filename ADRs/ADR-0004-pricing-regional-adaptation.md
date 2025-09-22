# ADR-0004 — Pricing & Regional Adaptation

## Status
Accepted ✅

## Context
DigitalMeve provides a unique global certification service, combining visible and invisible proof layers embedded directly into files (PDF, DOC, etc.), with independent verification mechanisms.  
To achieve global adoption, pricing must be:
- **Simple** (only 2 paid plans: Individuals & Professionals).
- **Accessible** (affordable monthly price points).
- **Globalized** (regional adaptation with taxes and currency support).
- **Compliant** with international standards on payments, refunds, and consumer rights.

## Decision
We adopt the following **pricing & payment strategy**:

### 1. Pricing Plans
- **Individuals**:  
  - €9.90 / month  
  - OR €99.00 / year (≈ 2 months free).  
  - Includes visible watermark, invisible SHA-256 + DigitalMeve key, and nominative info (name or email).  

- **Professionals**:  
  - €29.90 / month  
  - OR €299.00 / year.  
  - Includes:  
    - Visible watermark.  
    - Invisible SHA-256 + DigitalMeve key.  
    - Enterprise nominative data (company name, VAT ID, or official identifier).  
    - Private signing key for internal certification.  

### 2. Free Tier
- Free tier remains available with **limited certificates per month** and watermark.  
- No nominative data or enterprise features.  
- Designed for discovery and non-commercial use.  

### 3. Regional Adaptation
- Prices auto-adapted by country using **Stripe localized pricing API**.  
- Displayed in local currency (€, $, £, ¥, etc.).  
- VAT / GST auto-calculated and added where required.  
- Regulatory compliance with:  
  - EU VAT directives.  
  - US Sales tax rules.  
  - Local e-invoicing where mandatory.  

### 4. Payment Processing
- **Stripe** as the primary gateway.  
- Support for:  
  - Credit cards.  
  - Apple Pay / Google Pay.  
  - SEPA Direct Debit (EU).  
  - ACH (US).  
- All transactions are **encrypted (TLS 1.3)** and PCI DSS compliant.  
- No card data stored by DigitalMeve.  

### 5. Refunds & Guarantee
- **14-day no-question refund** for all new subscriptions (standard EU rule, applied worldwide).  
- Annual plans refundable pro-rata in case of downgrade or cancellation.  
- Stripe handles automatic prorated refunds.  

### 6. Billing & Invoicing
- Automatic invoices generated for each payment.  
- Invoices compliant with EU e-invoicing norms.  
- Company data (VAT ID, registration) included for Pro accounts.  

### 7. Security & Compliance
- Compliance with:  
  - **PCI DSS** (payment card security).  
  - **GDPR / CCPA** (data protection).  
  - **PSD2 / SCA** (Strong Customer Authentication in EU).  
- Multi-factor authentication enforced on Stripe dashboard.  
- No sensitive payment data stored locally.  

### 8. Future Evolution
- Family/Team plan (3–10 users) under consideration.  
- Enterprise plan (>100 certificates/month, SLA, on-prem key mgmt) will be defined later.  
- Potential crypto payments (BTC, ETH, stablecoins) may be added in roadmap v2, but not part of MVP.  

## Consequences
- DigitalMeve pricing is **aligned with global SaaS best practices** (clear tiers, psychological price points, compliance).  
- Adoption is facilitated by **localized pricing**, avoiding barriers for international users.  
- Regulatory compliance reduces legal risk.  
- Competitive positioning: simpler and cheaper than legal notary services, but more trusted than generic file timestamps.  

## References
- Stripe Global Pricing: https://stripe.com/pricing  
- EU Consumer Rights Directive (2011/83/EU)  
- PSD2 / SCA standards: https://www.ecb.europa.eu/paym/intro/legislation/html/index.en.html  
- PCI DSS overview: https://www.pcisecuritystandards.org
