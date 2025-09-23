# 🌍 DigitalMeve — Audit Global (v2)

Objectif : atteindre un niveau **≥ 9.5/10** en qualité produit & site, aligné sur les meilleures pratiques mondiales (Stripe, Apple, Notion…).

---

## 🔴 P0 — Priorité absolue (bloquant avant lancement)

### ✅ Produit & promesse
- Promesse claire : **watermark visible + preuve invisible + fichier original intact**.  
- Formats supportés : **PDF, DOCX, PNG, JPEG** (autres à venir).  
- Offre gratuite : **5 générations/mois max** → limiter abus via rate-limit & anti-spam.  
- Offre payante : inclut *issuer personnalisé*, DNS vérifiable, API dev.

### ✅ UX/UI
- Design cohérent (header, footer, mobile menu = 100%).  
- Page *Generate* simplifiée (pas technique, wording clair).  
- Animations fluides (fade/slide) cohérentes sur toutes pages.  
- Boutons avec état : idle / loading / success / error.  
- **Pas de scroll horizontal / écran noir sur mobile**.  

### ✅ Sécurité
- **Security headers** : CSP, HSTS, X-Frame-Options, etc.  
- Fichiers jamais stockés (traitement in-browser).  
- Logs anonymisés (pas d’email, pas de PII).  
- Anti-abus sur l’offre gratuite (rate limit + IP + captcha invisible).  

### ✅ Engineering
- **CI/CD** : lint → test → build → deploy.  
- Tests unitaires (Jest/RTL) + E2E (Playwright).  
- TypeScript strict (`noImplicitAny`, pas de `skipLibCheck`).  
- 0 warning build / runtime.  
- Code splitting, bundle analysé (<200kb/page critique).  

### ✅ Accessibilité
- Navigation clavier sur toutes pages (focus trap, skip links).  
- Contraste AA min (AAA si possible).  
- Labels ARIA cohérents.  
- Lecture écran testée (NVDA, VoiceOver).  

### ✅ Legal & Compliance
- Pages Terms, Privacy, Cookies → validées RGPD.  
- Consent manager (opt-in cookies).  
- Suppression données sur demande (droit à l’oubli).  
- Email support clair.  

---

## 🟡 P1 — Hautement recommandé (après stabilisation)

### 🛠 Produit & Formats
- Extensions futures : XLSX, PPTX, TXT, ODT.  
- SDK dev + API REST.  
- Page “Use cases” : preuves légales, diplômes, contrats.

### 🛠 Growth & SEO
- Open Graph & Twitter cards (image par défaut).  
- JSON-LD : Organization + Product + FAQ.  
- Sitemap & robots.txt validés.  
- Blog court avec exemples concrets.  

### 🛠 Viralité
- **Badge automatique** sur outputs : “Proof by DigitalMeve”.  
- Partage direct : bouton LinkedIn/Twitter après vérification.  
- Referral program (crédit gratuit si parrainage).  

### 🛠 Internationalisation
- FR / EN au lancement.  
- Localisation nombres, dates (Intl API).  
- Prix en €, $, £ avec TVA locale.  

### 🛠 Paiement & Legal
- Stripe checkout + factures PDF automatiques.  
- Politique remboursement claire.  
- Taxes incluses.  

### 🛠 Performance
- Images responsives (next/image).  
- Fonts preload + `font-display: swap`.  
- Lazy load sections hors viewport.  
- Lighthouse >95 mobile & desktop.  

---

## 🟢 P2 — Excellence continue

- Page *Status* + uptime monitor public.  
- Changelog auto-généré (semantic release).  
- Security.txt + hall of fame bug bounty.  
- Mode sombre clair auto.  
- Transitions micro-interactions (hover states premium).  
- Support mobile/tablette offline (PWA lite).  
- Sandbox dev publique (docs + exemples API).  
- Gamification : compteurs de preuves générées.  

---

## 📊 Score attendu

| Domaine             | Cible |
|---------------------|-------|
| UX/UI               | ≥ 9.5 |
| Accessibilité       | AAA   |
| Performance         | ≥ 95  |
| Sécurité            | 100% headers / RGPD |
| Produit & Viralité  | Top 5 mondial |
| Growth / SEO        | ≥ 90 Lighthouse |

---

## ✅ Prochaines étapes

1. Corriger **scroll bug mobile (global.css)**.  
2. Finaliser **page Generate** : wording simple, plus moderne.  
3. Implémenter **rate-limit free tier** (anti-abus).  
4. Ajouter **security headers** côté Next.js config.  
5. Lancer **tests E2E** sur flows principaux.  
6. Mettre à jour AUDIT toutes les semaines.  
