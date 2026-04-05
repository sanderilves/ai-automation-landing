# Action Plan — freeflowautomations.com/et/
**Generated:** 2026-04-05
**Current score: 68/100 — Estimated score after all fixes: ~85/100**

---

## 🔴 Critical — Fix immediately

### 1. Add `/et/` to sitemap.xml
**File:** `sitemap.xml`
**Why:** ET page not discoverable via sitemap on Google, Bing, or any AI platform. Only reachable through hreflang from EN page.
```xml
<url>
  <loc>https://freeflowautomations.com/et/</loc>
  <lastmod>2026-04-05</lastmod>
  <changefreq>monthly</changefreq>
  <priority>0.8</priority>
</url>
```
Also update EN entry lastmod to `2026-04-05`.

### 2. Sync FAQ schema answers to visible HTML
**File:** `et/index.html` (FAQPage JSON-LD block)
**Why:** At least the first FAQ answer is confirmed mismatched between schema and HTML ("tasuta kõne" vs "tasuta konsultatsioon"). Google requires exact match for FAQ rich results. Multiple copy edits since the schema was written mean several answers are likely diverged.
**Fix:** Go through all 6 FAQ items and copy the exact visible HTML answer text into the corresponding JSON-LD `"text"` field.

---

## 🟠 High — Fix within 1 week

### 3. Fix stale OG/Twitter descriptions on both pages
**Files:** `index.html`, `et/index.html`
**Why:** Social share previews (LinkedIn, X) use OG description. Both pages show outdated copy.

`index.html` — set `og:description` and `twitter:description` to:
> `FreeFlow Automations helps businesses automate repetitive processes — document management, client communication, reporting and much more.`

`et/index.html` — set `og:description` and `twitter:description` to:
> `FreeFlow Automations aitab ettevõtetel automatiseerida korduvaid protsesse — dokumendihaldus, kliendikommunikatsioon, aruandlus ja palju muud.`

### 4. Add `hreflang="x-default"` to both pages
**Files:** `index.html`, `et/index.html`
**Why:** Google best practice for multilingual sites.
```html
<link rel="alternate" hreflang="x-default" href="https://freeflowautomations.com/" />
```

### 5. Redirect `/et/index.html` → `/et/`
**File:** `netlify.toml`
**Why:** Both URLs return HTTP 200 with identical content — duplicate URL risk.
```toml
[[redirects]]
  from = "/et/index.html"
  to = "/et/"
  status = 301
  force = true
```

### 6. Update llms.txt
**File:** `llms.txt`
**Why:** Missing ET page URL (AI systems don't know Estonian version exists) and lacks machine-readable RSL 1.0 license header.
**Fix:** Add RSL 1.0 header, `dateModified`, and an Alternate Languages section:
```
# License: RSL 1.0 — retrieval and summarisation permitted, training not permitted
# dateModified: 2026-04-05

## Alternate languages
- Estonian (et): https://freeflowautomations.com/et/
```
Also update description and services to match current broader positioning (remove "debt collections" focus, update to "repetitive business processes").

### 7. Add company registration number to ET footer
**File:** `et/index.html`
**Why:** Estonian B2B buyers in regulated sectors routinely check e-äriregister. Missing registration number is a trust gap for the exact audience being targeted. One line in the footer: `Registrikood: XXXXXXXX`.

---

## 🟡 Medium — Fix within 1 month

### 8. Fix `WebSite inLanguage` in ET schema
**File:** `et/index.html` (first JSON-LD block, WebSite entity)
**Why:** WebSite entity represents the whole site — `inLanguage` should be `"en"`. Only the WebPage entity should have `"et"`.
**Fix:** Change WebSite `"inLanguage": "et"` → `"inLanguage": "en"`.

### 9. Update ET page `<title>` to match current positioning
**File:** `et/index.html`
**Why:** Title says "Reguleeritud Ettevõtetele" but copy has shifted to broader "ettevõtetele".
```html
<title>AI Automatiseerimine Ettevõtetele | FreeFlow Automations</title>
```

### 10. Add a concrete metric to the case study
**File:** `et/index.html` (and `index.html`)
**Why:** Section heading says "Päris tulemused" (real results) but no results are stated. This is the single biggest E-E-A-T gap and the highest-value AI citability improvement available without a full rewrite. Even a rough figure works: hours saved per week, number of automated interactions, manual steps eliminated.

### 11. Create an Estonian privacy policy page
**File:** New `et/privaatsuspoliitika.html` + update footer link in `et/index.html`
**Why:** GDPR Article 12 requires privacy information in language understandable to the data subject. Current privacy policy is English-only while the ET page explicitly targets Estonian-speaking businesses.

### 12. Add `datePublished` to WebPage schema on ET page
**File:** `et/index.html` (first JSON-LD block, WebPage entity)
**Why:** Alongside `dateModified`, gives Google a freshness signal.
```json
"datePublished": "2026-04-05"
```

### 13. Add sector targeting to visible body copy
**File:** `et/index.html`
**Why:** "Fintech, laenundus, kindlustus" appears in OG meta and schema but nowhere in visible body copy. Keyword gap between title/meta and body content.
**Fix:** Add one sentence to the Section 2 offer box or case study intro naming target sectors.

---

## 🟢 Low — Backlog

### 14. Add missing image attributes to EN founder photo
**File:** `index.html` (founder section)
```html
<img src="Sander_Ilves.jpg" alt="Sander Ilves, founder of FreeFlow Automations" width="160" height="160" loading="lazy" />
```

### 15. Add HSTS `includeSubDomains; preload`
**File:** `netlify.toml` headers config
**Why:** Enables HSTS preload list eligibility.

### 16. Verify `/privacy-policy` URL returns 200
**Why:** Sitemap lists `/privacy-policy` (no `.html`) — confirm it doesn't 404.

### 17. Build AI citation signals (long-term)
**Why:** No Wikipedia, no YouTube, no Reddit — these are the three strongest LLM citation signals.
- Publish a workflow demo video on YouTube (highest ROI: embed on page, add VideoObject schema)
- Participate genuinely in r/n8n, r/automation — answer questions, share case study
- Seek coverage in Äripäev, Delfi Ärileht, The Baltic Times for Wikipedia eligibility
