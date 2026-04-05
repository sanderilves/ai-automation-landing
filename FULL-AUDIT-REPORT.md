# SEO Audit Report — FreeFlow Automations
**URL:** https://freeflowautomations.com  
**Date:** 2026-04-04  
**Business type:** B2B AI automation consultancy (service area business — Baltic States)  
**Auditor:** Claude Code SEO Audit

---

## SEO Health Score: 75 / 100

| Category | Weight | Score | Weighted |
|---|---|---|---|
| Technical SEO | 22% | 78 | 17.2 |
| Content Quality | 23% | 68 | 15.6 |
| On-Page SEO | 20% | 75 | 15.0 |
| Schema / Structured Data | 10% | 72 | 7.2 |
| Performance (CWV) | 10% | 85 | 8.5 |
| AI Search Readiness | 10% | 80 | 8.0 |
| Images | 5% | 65 | 3.2 |
| **Total** | | | **74.7** |

---

## Executive Summary

FreeFlow Automations has a technically solid single-page site: correct canonical, sitemap, well-configured robots.txt (including AI crawlers), security headers, schema markup, and a lightweight page with fast load characteristics. The **llms.txt** file is a genuine differentiator for AI search visibility.

The main gaps are in **content depth and social proof**. A single anonymous case study with vague metrics limits trust and E-E-A-T signals. There are no client testimonials, no measurable results, and no named clients — which matters for a B2B consultancy selling to regulated businesses. Schema is good but incomplete (missing image, logo, hasOfferCatalog). Two image optimisation issues (missing `width`/`height` and `loading="lazy"` on the founder photo) may affect CLS and LCP scores.

### Top 5 Critical Issues
1. No client testimonials or named social proof
2. Meta description 176 chars (over 160 recommended) — likely truncated in SERPs
3. Founder photo missing `width`, `height`, and `loading="lazy"` — CLS risk
4. Schema missing `image`, `logo`, and `hasOfferCatalog` on ProfessionalService
5. CSP is report-only — provides no actual XSS protection

### Top 5 Quick Wins
1. Add `width="160" height="160" loading="lazy"` to founder photo (2-min fix, CLS improvement)
2. Shorten meta description to under 160 chars
3. Change nav logo `href="#"` to `href="/"` (crawlability + UX)
4. Add `image` and `logo` to ProfessionalService schema
5. Add HSTS header to netlify.toml

---

## Technical SEO

### Crawlability
| Check | Status | Notes |
|---|---|---|
| robots.txt | ✓ Pass | Allows all crawlers including GPTBot, ClaudeBot, PerplexityBot, OAI-SearchBot |
| Sitemap declared in robots.txt | ✓ Pass | Correct URL |
| Canonical tag | ✓ Pass | `https://freeflowautomations.com/` |
| Redirect from `/privacy-policy.html` | ✓ Pass | 301 configured in netlify.toml |
| Nav logo href | ⚠ Warn | Links to `#` instead of `/` — minor crawlability signal |

### Indexability
| Check | Status | Notes |
|---|---|---|
| Google site verification | ✓ Pass | Meta tag present |
| No noindex found | ✓ Pass | |
| Sitemap URLs | ✓ Pass | Homepage + privacy-policy listed |
| Sitemap lastmod date | ✓ Pass | 2026-04-03 (current) |

### Security Headers (netlify.toml)
| Header | Status | Notes |
|---|---|---|
| X-Frame-Options | ✓ DENY | |
| X-Content-Type-Options | ✓ nosniff | |
| Referrer-Policy | ✓ strict-origin-when-cross-origin | |
| Permissions-Policy | ✓ Pass | camera, microphone, geolocation locked |
| Content-Security-Policy | ⚠ Report-Only | Not enforced — no XSS protection |
| Strict-Transport-Security (HSTS) | ✗ Missing | Add to netlify.toml |

---

## Content Quality (E-E-A-T)

### Experience & Expertise
- Founder credentials detailed: Industrial Engineering degree, MSc Organisational Behaviour, Autoliv, startup co-founder — strong expertise signals
- Real case study showing actual built workflow (with screenshot) — good experience signal
- Technology stack named specifically (n8n, Claude API, Python) — demonstrates expertise

### Authoritativeness
- LinkedIn profile linked — external authority signal
- No client testimonials — **significant gap** for a B2B services site
- Case study client unnamed — reduces credibility
- No partner badges, certifications, or press mentions

### Trustworthiness
- Phone number, email, and physical address present — strong trust signals
- GDPR mention in FAQ — relevant for regulated industry clients
- Privacy policy linked in footer
- No `tel:` or `mailto:` schema markup in footer links (they're HTML anchors but not schema-linked)

### Readability
- Clear, direct writing style at ~10th grade reading level — appropriate for B2B
- Problem/solution framing is effective
- Section labelling (eyebrow labels) aids navigation
- FAQ adds useful depth

### Thin Content Risks
- Single page — no blog, no service detail pages, no industry pages
- "Reducing manual processing time significantly" in founder bio lacks specifics — vague
- Case study outcome metrics not quantified (%, hours saved, €)

---

## On-Page SEO

| Element | Value | Status |
|---|---|---|
| Title | "AI Automation for Regulated Businesses \| FreeFlow Automations" (57 chars) | ✓ Good |
| Meta description | 176 chars | ⚠ Too long (>160) |
| H1 | "Your specialists are doing work that software should be doing." | ✓ Good (unique, compelling) |
| H2s | Multiple — "Automation built for regulated businesses", "Three steps from production", etc. | ✓ Good |
| H3s | Service cards and step names | ✓ Good |
| Canonical | `https://freeflowautomations.com/` | ✓ Good |
| Lang attribute | `lang="en"` | ✓ Good |
| OG tags | og:type, og:url, og:title, og:description, og:image | ✓ Complete |
| Twitter Card | summary_large_image with all required tags | ✓ Complete |
| `<main>` element | Missing | ⚠ Accessibility/semantic gap |
| Internal linking | Only `#cta` anchor and `#` for logo | ⚠ Limited |

**Meta description (current — 176 chars):**
> FreeFlow Automations helps fintech, lending, and insurance businesses in the Baltic States automate compliance workflows, document processing, and customer onboarding using AI.

Should be trimmed to ~150-155 chars.

---

## Schema / Structured Data

### What's implemented
- `@graph` with linked entities: ProfessionalService, Person, WebSite, WebPage, 4× Service
- FAQPage with 6 questions
- GeoCoordinates (lat/long for Tallinn)
- `areaServed` with Baltic States and Europe
- `sameAs` linking to LinkedIn

### Issues Found

| Issue | Severity |
|---|---|
| `ProfessionalService` missing `image` property | High |
| `ProfessionalService` missing `logo` property | High |
| `ProfessionalService` missing `hasOfferCatalog` linking Service entities | Medium |
| `ProfessionalService` missing `priceRange` | Low |
| `ProfessionalService` missing `openingHours` | Low |
| `PostalAddress` missing `streetAddress` | Low |
| `Service` nodes use `areaServed: "Baltic States"` (string) instead of Place object | Low |
| FAQPage answer text differs slightly from visible HTML | Low |

### Schema validation
The `FAQPage` schema answer text is longer/different from the visible `<details>` text. While Google uses the schema, discrepancy can cause validation warnings. The visible FAQ text is condensed vs. schema text.

---

## Performance (Core Web Vitals estimate)

Site characteristics:
- Pure HTML/CSS/JS — no framework overhead
- All CSS inline in `<style>` block — zero render-blocking stylesheets
- No external JS libraries
- Two images in viewport path: workflow.png (lazy ✓) and Sander_Ilves.jpg (not lazy ✗)

| Metric | Estimate | Notes |
|---|---|---|
| LCP | Likely Good (<2.5s) | Lightweight page, text-based hero, no hero image |
| INP | Likely Good (<200ms) | Minimal JS (only lightbox onclick) |
| CLS | Risk present | Sander_Ilves.jpg has no width/height — layout shift possible |
| TTFB | Likely Good | Netlify CDN |

### Image issues affecting performance
1. `Sander_Ilves.jpg` — missing `width="160" height="160"` attributes → CLS risk
2. `Sander_Ilves.jpg` — missing `loading="lazy"` → unnecessary eager load for below-fold image
3. Images are PNG/JPG — no WebP/AVIF served (Netlify does not auto-convert)

---

## Images

| Image | Alt text | width/height | loading | Format |
|---|---|---|---|---|
| `workflow.png` | ✓ "Debt collections automation workflow built in n8n" | ✓ 800×279 | ✓ lazy | PNG |
| `Sander_Ilves.jpg` | ✓ "Sander Ilves, founder of FreeFlow Automations" | ✗ Missing | ✗ Missing | JPG |
| `og-image.png` | N/A (meta only) | N/A | N/A | PNG |

---

## AI Search Readiness

### Strengths
- `llms.txt` present and well-structured — describes company, services, tech stack, contact
- robots.txt explicitly allows: `GPTBot`, `ClaudeBot`, `PerplexityBot`, `Google-Extended`, `OAI-SearchBot`
- FAQPage schema — AI systems can extract structured Q&A
- Specific, factual content (Tallinn location, n8n/Claude/Python stack, named industries)
- `retrieval_permissions` section in llms.txt is correctly set

### Gaps
- `llms.txt` does not include the case study details — AI can't summarise your proof of work
- No quantified statistics anywhere on the page (AI systems prefer citable numbers)
- No "About" or "methodology" page for deeper AI retrieval
- `llms.txt` could include a short FAQ section mirroring the page FAQ

---

## Local SEO

This is primarily a digital/remote service business (SAB serving Baltic States) so classic local SEO is secondary, but:

| Check | Status |
|---|---|
| Physical address present | ✓ Tallinn, Estonia |
| Phone number present | ✓ +372 58 133 551 |
| Email present | ✓ sander@freeflowautomations.com |
| GeoCoordinates in schema | ✓ |
| Google Business Profile | Unknown (not detectable from code) |
| NAP consistency | ✓ Consistent across footer and schema |
| Local keyword targeting | ⚠ "Baltic States" mentioned but not individually targeted (Estonia, Latvia, Lithuania) |

---

## Files Checked

```
index.html          — Full read
robots.txt          — Full read
sitemap.xml         — Full read
netlify.toml        — Full read
llms.txt            — Full read
CLAUDE.md           — Full read
```
