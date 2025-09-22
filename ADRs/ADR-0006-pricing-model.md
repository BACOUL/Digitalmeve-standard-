# ADR-0006: Global Pricing Model for DigitalMeve

## Status
Accepted

## Context
DigitalMeve is positioned as the **global certification standard** for documents, integrating both visible and invisible proofs.  
For credibility and sustainability, the project needs a **clear, transparent, and fair pricing model** that balances:

- **Accessibility** → low entry cost for individuals.  
- **Professional value** → advanced features and guarantees for businesses.  
- **Global compliance** → legal alignment with payment regulations (e.g., PSD2 in Europe, PCI-DSS, consumer protection rules).  
- **Scalability** → Stripe-based billing, supporting multiple currencies and automatic tax/VAT handling.  

Existing models in global SaaS and security standards were analyzed:
- Adobe Acrobat (subscription model).  
- DocuSign (per-user pricing tiers).  
- OpenSSL/Let’s Encrypt (free, but funded externally).  

DigitalMeve requires **hybrid sustainability** → accessible pricing with premium layers.  

## Decision
Adopt a **two-tier subscription model**:

1. **Individuals**  
   - €9.90/month (or discounted annual plan).  
   - Includes: watermarking, invisible SHA-256 proof, invisible DigitalMeve signature.  
   - Premium users: name or email embedded into certificate.  

2. **Professionals**  
   - €29.90/month (or discounted annual plan).  
   - Includes all individual features **plus**:  
     - Private key for enterprise signing.  
     - Certificate embedding with enterprise name/reference.  
     - Invisible enterprise patch for reinforced authenticity.  

### Billing Infrastructure
- **Stripe** as the global payment gateway.  
- Support for **local currencies** (EUR, USD, GBP, etc.) via Stripe multi-currency.  
- **Regional adaptation** (prices adjusted for purchasing power parity where required).  
- Compliance: PCI-DSS, GDPR, SCA/3D Secure (Europe).  
- Refunds: 14-day standard refund policy (aligned with EU and international norms).  

### Pricing Governance
- Prices are **public and documented**.  
- Changes require a new ADR, reviewed by the **Technical Steering Committee (TSC)**.  
- Annual audits ensure compliance with consumer protection standards in all target markets.  

## Alternatives Considered
- **Free for all**  
  - ✅ Maximizes adoption.  
  - ❌ No sustainability, no enterprise trust → rejected.  

- **High enterprise-only pricing**  
  - ✅ High margins.  
  - ❌ Blocks individual adoption, weak network effect → rejected.  

- **Per-document pricing**  
  - ✅ Usage-based fairness.  
  - ❌ Complex integration, discourages adoption → rejected.  

## Consequences
- Clear and predictable model: €9.90 for individuals, €29.90 for professionals.  
- Stripe ensures **scalable, compliant billing worldwide**.  
- Adoption path is open to all while ensuring **financial sustainability**.  
- Enterprise trust increases due to formal guarantees and cryptographic control.  

## References
- [Stripe Global Payments](https://stripe.com/global)  
- [PCI-DSS Compliance](https://www.pcisecuritystandards.org/)  
- [EU Consumer Protection Rules](https://commission.europa.eu/strategy-and-policy/consumers/consumer-protection_en)  
- Adobe & DocuSign pricing models (benchmark).
