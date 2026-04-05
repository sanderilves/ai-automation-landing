# SEO Action Plan — FreeFlow Automations
**Generated:** 2026-04-04  
**Based on:** FULL-AUDIT-REPORT.md

---

## Critical (fix immediately)

### 1. Add social proof / testimonials
**Why:** A B2B consultancy selling to regulated businesses lives or dies on trust. One anonymous case study with no metrics is the biggest E-E-A-T gap on the site.  
**How:**
- Add 2-3 short testimonial quotes from past clients (even first-name + company type if full name not permitted)
- Add specific metrics to the case study: hours saved per week, % reduction in manual work, time-to-deploy
- Consider naming the case study client if possible (even "a Baltic fintech" is fine, but "Bondora" or "Monese" would be stronger)

---

### 2. Shorten meta description
**Current (176 chars):**  
`FreeFlow Automations helps fintech, lending, and insurance businesses in the Baltic States automate compliance workflows, document processing, and customer onboarding using AI.`

**Suggested (~151 chars):**  
`AI automation for fintech, lending, and insurance businesses in the Baltic States. We automate compliance workflows, document processing, and onboarding.`

**File:** `index.html` line 7

---

## High (fix within 1 week)

### 3. Fix founder photo attributes
**File:** `index.html` line 946  
**Current:** `<img src="Sander_Ilves.jpg" alt="Sander Ilves, founder of FreeFlow Automations" />`  
**Fix:** `<img src="Sander_Ilves.jpg" alt="Sander Ilves, founder of FreeFlow Automations" width="160" height="160" loading="lazy" />`

### 4. Fix nav logo href
**File:** `index.html` line 746  
**Current:** `<a class="nav-logo" href="#">FreeFlow Automations</a>`  
**Fix:** `<a class="nav-logo" href="/">FreeFlow Automations</a>`

### 5. Add image and logo to ProfessionalService schema
**File:** `index.html` — schema block starting line 590  
Add inside the ProfessionalService entity:
```json
"image": "https://freeflowautomations.com/og-image.png",
"logo": {
  "@type": "ImageObject",
  "url": "https://freeflowautomations.com/favicon.png"
}
```

### 6. Add HSTS header to netlify.toml
Add to the `[headers.values]` block under `for = "/*"`:
```toml
Strict-Transport-Security = "max-age=31536000; includeSubDomains"
```

### 7. Enforce CSP (or remove report-only)
**Current:** `Content-Security-Policy-Report-Only` — no actual protection  
**Fix:** Change to `Content-Security-Policy` (after testing that the policy doesn't break the Calendly link):
```toml
Content-Security-Policy = "default-src 'self'; script-src 'self' 'unsafe-inline' https://calendly.com; frame-src https://calendly.com; img-src 'self' data: https:; style-src 'self' 'unsafe-inline';"
```

---

## Medium (fix within 1 month)

### 8. Add `<main>` element wrapping page content
Wrap all `<section>` elements in `<main>` for semantic HTML and accessibility.

### 9. Enrich llms.txt with case study and FAQ
Add a section to `llms.txt`:
```
## Case study

Built a debt collections automation workflow for a Baltic fintech. The workflow
automatically identifies customers to contact each day, checks contact windows,
routes routine cases to an AI voice agent, escalates complex cases to humans,
and logs every interaction for compliance without manual effort.

## FAQ

**How long does it take?** Most automations are live within 2-4 weeks.
**Do I need technical knowledge?** No. Automations run in the background.
**Is my data safe?** Yes. GDPR-compliant, no data stored on third-party servers without approval.
```

### 10. Add hasOfferCatalog to ProfessionalService schema
Link the existing Service entities via `hasOfferCatalog`:
```json
"hasOfferCatalog": {
  "@type": "OfferCatalog",
  "name": "AI Automation Services",
  "itemListElement": [
    { "@id": "https://freeflowautomations.com/#service-document-processing" },
    { "@id": "https://freeflowautomations.com/#service-onboarding" },
    { "@id": "https://freeflowautomations.com/#service-compliance" },
    { "@id": "https://freeflowautomations.com/#service-collections" }
  ]
}
```

### 11. Add quantified metrics to case study and founder bio
Replace vague statements like "reducing manual processing time significantly" with specific numbers. Examples:
- "reduced manual processing time by 80%"  
- "eliminated 4+ hours of manual CRM updates per day"  
- "deployed in 12 days"

### 12. Add individual country targeting
The Baltic States market (Estonia, Latvia, Lithuania) is mentioned collectively but not individually targeted. Consider:
- Adding Estonia, Latvia, Lithuania to `areaServed` in schema as separate Place objects
- Mentioning all three countries by name in the hero or intro copy

---

## Low (backlog)

### 13. Convert images to WebP
- `Sander_Ilves.jpg` → `Sander_Ilves.webp` with JPG fallback
- `workflow.png` → `workflow.webp` with PNG fallback  
Use `<picture>` element for progressive enhancement.

### 14. Add `openingHours` and `priceRange` to schema
Not critical for a digital services business but helps local search.

### 15. Add `streetAddress` to PostalAddress schema
Even a vague address like "Viru väljak 2" or just the district helps for local verification.

### 16. Align FAQPage schema text with visible HTML
The schema `acceptedAnswer` text for some FAQs is longer/different from the `<details>` visible text. Make them identical to avoid Google validation warnings.

### 17. Add Google Business Profile
Create and verify a Google Business Profile for "FreeFlow Automations" in Tallinn to support local search appearances even for a digital services business.

---

## Scoring Impact Estimate

| Fix | Category | Score Impact |
|---|---|---|
| Testimonials + case study metrics | Content Quality | +8-12 pts |
| Schema image/logo/hasOfferCatalog | Schema | +5-8 pts |
| Founder photo attributes | Performance | +3-5 pts |
| CSP enforcement | Technical | +3 pts |
| HSTS header | Technical | +2 pts |
| Meta description | On-Page | +2 pts |
| llms.txt enrichment | AI Search | +4-6 pts |

**Potential score after all Critical + High fixes: ~82/100**
