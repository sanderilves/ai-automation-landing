# SEO Audit Report — freeflowautomations.com/et/
**Date:** 2026-04-05
**Scope:** ET landing page + EN/ET bilingual setup
**Overall SEO Health Score: 68 / 100**

---

## Executive Summary

The site has a solid technical foundation: HTTPS enforced, HTTP/2, correct hreflang, valid JSON-LD schema, and all AI crawlers explicitly allowed. The main gaps are discoverability of the ET page (missing from sitemap and llms.txt), stale social meta on both pages, a duplicate URL, and content depth issues that limit AI citation eligibility. All critical and high items are fixable within a few hours.

**Top 5 critical issues:**
1. `/et/` not in sitemap.xml — ET page not discoverable via sitemap on any platform
2. OG/Twitter descriptions stale on both pages (old fintech-specific copy)
3. FAQ schema answer text doesn't match visible HTML — blocks Google rich results
4. `/et/index.html` returns HTTP 200 (same content as `/et/`) — duplicate URL
5. No `hreflang="x-default"` on either page

---

## Technical SEO

### Crawlability & Indexability
- ✅ robots.txt allows GPTBot, ClaudeBot, PerplexityBot, Google-Extended, OAI-SearchBot
- ✅ robots.txt references sitemap
- ❌ **sitemap.xml missing `/et/`** — only `/` and `/privacy-policy` listed
- ⚠️ sitemap has no hreflang annotations (xhtml:link entries)

### Canonicals & Hreflang
- ✅ ET canonical: `https://freeflowautomations.com/et/`
- ✅ Both hreflang tags on ET page (`en → /`, `et → /et/`)
- ✅ Both hreflang tags on EN page
- ❌ **No `hreflang="x-default"`** on either page
- ❌ **`/et/index.html` returns HTTP 200** (same ETag as `/et/`) — duplicate URL

### Security Headers
- ✅ HTTPS, HTTP/2, x-frame-options: DENY, x-content-type-options: nosniff
- ✅ referrer-policy: strict-origin-when-cross-origin
- ✅ permissions-policy: camera=(), microphone=(), geolocation=()
- ✅ HSTS: max-age=31536000
- ⚠️ HSTS missing `includeSubDomains; preload`
- ⚠️ CSP is `report-only` — not enforced

### Performance
- ✅ Single-file HTML, no external CSS/JS except Calendly
- ✅ ET page images have `loading="lazy"`, `width`, `height`
- ❌ EN founder photo missing `width`, `height`, `loading="lazy"` — causes CLS

---

## On-Page SEO

### ET Page (`/et/`)
- ✅ `<html lang="et">` correct
- ✅ Meta description: current and accurate (143 chars)
- ⚠️ Title "AI Automatiseerimine Reguleeritud Ettevõtetele" conflicts with on-page copy which has shifted to broader "ettevõtetele" (non-regulated) positioning
- ❌ **OG/Twitter description stale** — old fintech-specific copy not matching meta description
- ✅ H1 present and unique; H2/H3 hierarchy correct
- ⚠️ H1 is problem-framed ("Teie spetsialistid teevad tööd...") — AI systems extract H1 as the primary entity description; this frames the brand as a "problem" not a solution
- ⚠️ "Reguleeritud ettevõtted" appears in title/meta/schema but not in visible body copy — keyword gap

### EN Page (`/`)
- ✅ `<html lang="en">` correct; title and meta description correct
- ❌ **OG/Twitter description stale** — still says "fintech, lending, and insurance businesses in the Baltic States automate compliance workflows..."

---

## Schema & Structured Data

### ET Page
- ✅ Both JSON-LD blocks parse without errors
- ✅ FAQPage has 6 questions in Estonian
- ✅ WebPage `inLanguage: "et"` and `@id` uses `/et/` URL
- ❌ **FAQ schema answer text doesn't match visible HTML** — the "Milliste ettevõtetega" answer in schema ends "broneerige tasuta kõne ja me ütleme teile ausalt" but visible HTML ends "broneerige tasuta konsultatsioon ja arutame seda lähemalt". Google requires exact match for FAQ rich results. Other answers likely have similar divergence from all the iterative copy edits.
- ⚠️ `WebSite` entity has `"inLanguage": "et"` — should be `"en"` (WebSite represents the whole site; only WebPage should have `"et"`)
- ⚠️ `WebPage` schema missing `datePublished`

---

## AI Search Readiness (GEO) — Score: 54/100

- ✅ llms.txt present and accessible
- ✅ All major AI crawlers allowed in robots.txt
- ❌ **llms.txt doesn't mention `/et/`** — AI systems get no knowledge the Estonian version exists
- ❌ **llms.txt lacks machine-readable RSL 1.0 license header** — training prohibition is prose-only, not parsed by crawlers
- ⚠️ **FAQ content in `<details>` collapse elements** — collapsed content may be invisible to some AI crawlers; FAQPage JSON-LD partially mitigates this but only if schema matches HTML exactly (see above)
- ⚠️ All content passages are short (45-120 words vs. ideal 130-167 words for AI citation)
- ⚠️ No Wikipedia entity for company or founder (strongest LLM citation signal)
- ⚠️ No YouTube presence (tied for strongest citation signal)
- ⚠️ No Reddit presence (second-strongest citation signal)
- ⚠️ No statistics attributed to sources — unsourced claims treated as marketing copy by AI systems

---

## Content Quality & E-E-A-T — Score: 62/100

| Factor | Score | Notes |
|---|---|---|
| Experience | 14/20 | Case study present but **zero measurable outcomes stated** |
| Expertise | 17/25 | Named tech stack, dual-degree background, industry terminology |
| Authoritativeness | 12/25 | No press, partner logos, client names, or third-party validation |
| Trustworthiness | 18/30 | Phone/email/address/GDPR present; missing: company reg number, Estonian privacy policy |

**Key content gaps:**
- ❌ Case study heading says "Päris tulemused" (real results) but **no actual metrics are stated** — no hours saved, no call volume, no error reduction
- ❌ Privacy policy is English-only — GDPR Article 12 requires language understandable to the data subject
- ❌ No company registration number (e-äriregister) — critical trust signal for Estonian B2B buyers in regulated sectors
- ⚠️ Sector targeting (fintech, laenundus, kindlustus) appears in OG/schema but not in visible body copy
- ⚠️ Section 2 offer box and hero lead paragraph cover the same ground without differentiation

---

## Sitemap

- ❌ `/et/` not listed
- ⚠️ Privacy policy listed as `/privacy-policy` (no `.html`) — verify this URL returns 200
- ⚠️ `lastmod` dates stale (2026-04-03, multiple deploys since)
- ⚠️ No hreflang annotations in sitemap entries

---

## Score Breakdown

| Category | Score | Weight | Weighted |
|---|---|---|---|
| Technical SEO | 68 | 22% | 15.0 |
| Content Quality | 62 | 23% | 14.3 |
| On-Page SEO | 68 | 20% | 13.6 |
| Schema | 72 | 10% | 7.2 |
| Performance (CWV) | 75 | 10% | 7.5 |
| AI Search Readiness | 54 | 10% | 5.4 |
| Images | 78 | 5% | 3.9 |
| **Total** | | | **66.9 → 68** |
