# Canonical Tags — Technical SEO Playbook

## When to Use This

Use this playbook when:
- Duplicate content issues are suspected or confirmed
- Multiple URL variations of the same content exist (www/non-www, http/https, trailing slash, parameters)
- E-commerce sites with faceted navigation or product variants
- Syndicated content appears on multiple domains
- Paginated content needs canonical treatment
- After a site migration where old URLs still exist alongside new ones
- GSC shows multiple versions of the same page getting indexed
- Screaming Frog or Ahrefs reports canonical chain or canonical loop errors

---

## Core Concept

The canonical tag tells Google: "This page has duplicate versions — THIS is the one you should index and pass authority to."

```html
<!-- Placed in <head> of the page -->
<link rel="canonical" href="https://www.domain.com/preferred-url/" />
```

Google treats this as a strong hint, not a directive (unlike `noindex`). If you have other strong conflicting signals (e.g., many internal links pointing to a different version), Google may override your canonical.

---

## Step-by-Step Checklist

### 1. Identify Duplicate URL Variations
Common sources of duplicates:
- Protocol: `http://domain.com` vs `https://domain.com`
- www vs non-www: `www.domain.com` vs `domain.com`
- Trailing slash: `/page/` vs `/page`
- Parameter variations: `/page?utm_source=email` vs `/page`
- Session IDs: `/page?sessionid=abc123`
- Sorting/filtering: `/products?sort=price&order=asc`
- Print versions: `/page?print=1` or `/print/page/`
- Uppercase/lowercase: `/Page` vs `/page`

Run Screaming Frog and export the "Canonicals" tab to identify all canonical relationships.

### 2. Set Self-Referencing Canonicals on All Indexable Pages
Every page should declare itself as canonical (or point to the preferred version):
```html
<head>
  <link rel="canonical" href="https://www.domain.com/exact-url-of-this-page/" />
</head>
```
- URL must be absolute (full URL, not relative path)
- Must match the preferred protocol and domain exactly
- Must match the preferred trailing slash convention exactly

### 3. Implement Cross-Domain Canonicals for Syndicated Content
If the same article appears on your site AND a third-party site (e.g., guest post, news syndication):
- The original source should have a self-referencing canonical
- The syndicated copy should point back to the original:
  ```html
  <!-- On the syndicated/copy page -->
  <link rel="canonical" href="https://www.original-source.com/original-article/" />
  ```
- This prevents the syndicated copy from outranking the original

### 4. Handle E-Commerce Faceted Navigation
Product listings with faceted filters create hundreds of near-duplicate pages:

**Strategy A — Canonical to base category page (most common):**
```html
<!-- On /products/shoes?color=red&size=10 -->
<link rel="canonical" href="https://www.domain.com/products/shoes/" />
```

**Strategy B — Canonical to most relevant filtered page (if filter has real SEO value):**
```html
<!-- /products/shoes/red/ is a real target keyword page -->
<link rel="canonical" href="https://www.domain.com/products/shoes/red/" />
```

**Strategy C — Use robots.txt to prevent crawling (simpler for large catalogs):**
```
Disallow: /*?color=
Disallow: /*?size=
```
Choose based on whether the filtered URL targets a real keyword with search volume.

### 5. Audit for Canonical Chains
A canonical chain occurs when Page A canonicals to Page B, which canonicals to Page C.
Google will follow chains but it's inefficient and may ignore the chain altogether.

Detection: Screaming Frog > Canonicals > Filter "Canonical Chain"

Fix: Update Page A to point directly to Page C (the final destination):
```html
<!-- BEFORE: chain -->
<!-- Page A → canonical to Page B → canonical to Page C -->

<!-- AFTER: fixed -->
<!-- Page A canonical directly to Page C -->
<link rel="canonical" href="https://www.domain.com/page-c/" />
```

### 6. Audit for Canonical Loops
A → B and B → A (pointing at each other) — Google ignores both.

Detection: Screaming Frog will flag these as "Canonical Loop"

Fix: Decide which is the preferred URL, set that page to self-reference, update the other to point to it.

### 7. Ensure Canonical Matches Other Signals
Canonical tags work best when ALL signals agree. Check consistency of:
- 301 redirect: Non-canonical versions should 301 redirect to the canonical URL
- Sitemap: Only include canonical URLs in sitemap.xml
- Internal links: All internal links should point to the canonical URL version
- hreflang: `href` values in hreflang tags must be the canonical versions

```html
<!-- Consistent signals example for /page/ (canonical with trailing slash) -->

<!-- 1. Canonical tag on page -->
<link rel="canonical" href="https://www.domain.com/page/" />

<!-- 2. 301 redirect: /page → /page/ (server config) -->

<!-- 3. Sitemap entry -->
<loc>https://www.domain.com/page/</loc>

<!-- 4. Internal links point to /page/ not /page -->
<a href="/page/">Page Name</a>
```

### 8. Handle Pagination Canonical Treatment
For paginated series (/blog/, /blog/page/2/, /blog/page/3/):

**Option A (recommended):** Self-canonicalize each page (each page is its own canonical)
```html
<!-- On /blog/page/2/ -->
<link rel="canonical" href="https://www.domain.com/blog/page/2/" />
```

**Option B (outdated but still used):** Canonical all pages to page 1
```html
<!-- LESS RECOMMENDED — hides page 2+ content from indexing -->
<link rel="canonical" href="https://www.domain.com/blog/" />
```
Use Option A for paginated content with unique valuable listings. Use Option B only if page 2+ has no independent SEO value.

### 9. Validate Canonical Implementation for HTTP/HTTPS and WWW/non-WWW
- All canonical tags must use the preferred protocol and domain consistently
- If preferred: `https://www.domain.com` — every canonical must start with `https://www.`
- Mixed protocols in canonicals = Google may ignore them

Check with:
```bash
# Test canonical in page source
curl -s https://www.domain.com/page/ | grep -i canonical
# Should return: <link rel="canonical" href="https://www.domain.com/page/">
```

### 10. Audit Canonical Tags in JavaScript-Rendered Pages
- If canonical tag is injected by JavaScript, Google may not process it reliably
- Use Screaming Frog with JavaScript rendering enabled to verify canonical is present in rendered output
- Best practice: Include canonical in server-rendered HTML `<head>`, not JS-injected

### 11. Check for Canonicals Pointing to noindex Pages
If Page A canonicals to Page B, but Page B has `noindex`:
- Page A's canonicalization is void — Google may index Page A instead, or neither
- Fix: Ensure canonical target is always an indexable page
- Run: Screaming Frog > Canonicals > export and cross-reference with noindex pages

### 12. Implement and Validate hreflang with Canonical for Multilingual Sites
Canonical and hreflang must work together:
```html
<head>
  <!-- English canonical -->
  <link rel="canonical" href="https://www.domain.com/en/page/" />
  
  <!-- hreflang declarations -->
  <link rel="alternate" hreflang="en" href="https://www.domain.com/en/page/" />
  <link rel="alternate" hreflang="es" href="https://www.domain.com/es/pagina/" />
  <link rel="alternate" hreflang="x-default" href="https://www.domain.com/en/page/" />
</head>
```
- Canonical points to the current page's own language version
- Do NOT canonical all language versions to the English page

---

## Common Issues and Fixes

| Issue | Symptom | Fix |
|-------|---------|-----|
| Missing canonical | Duplicate versions indexed; authority diluted | Add self-referencing canonical to all pages |
| Canonical chain (A→B→C) | Crawl inefficiency; canonical may be ignored | Update A to point directly to C |
| Canonical loop (A↔B) | Both versions may be ignored | Pick one as canonical; self-reference it; redirect the other |
| Canonical to noindex page | Target page suppressed; source page may not index | Fix canonical target to an indexable page |
| Mixed http/https in canonicals | Inconsistent signals | Standardize all canonicals to `https://` |
| JS-injected canonical | Googlebot may miss it | Move to server-rendered HTML `<head>` |
| Canonical conflicts with 301 | One version redirects to non-canonical destination | Align redirect destination with canonical URL |
| Wrong canonical on faceted pages | Facets indexed as standalone pages; category diluted | Set canonical on facets to base category URL |

---

## Tools to Use

| Tool | Purpose |
|------|---------|
| Screaming Frog | Canonical audit, chain detection, loop detection |
| Google Search Console | URL Inspection (see which version Google selected as canonical) |
| Ahrefs Site Audit | Canonical issues report |
| curl + grep | Manual canonical tag inspection |
| Google Search Console > URL Inspection | "Google-selected canonical" vs "User-declared canonical" |
| Semrush Site Audit | Duplicate content and canonical issues |

---

## How to Measure Success

**Key GSC signal:** URL Inspection > "Google-selected canonical" should match "User-declared canonical." If Google overrides your canonical, investigate why (mixed signals, poor page quality, thin content).

**Baseline metrics:**
- Count of pages with canonical errors (Screaming Frog)
- Count of canonical chains
- Count of canonical loops
- Count of pages with no canonical tag
- GSC: pages where Google is selecting a different canonical than declared

**30-day targets:**
- [ ] All indexable pages have a canonical tag (zero missing)
- [ ] Zero canonical chains (all canonicalize directly to final URL)
- [ ] Zero canonical loops
- [ ] All canonical targets are live, indexable, 200-status pages
- [ ] Canonical consistently uses preferred protocol/www version

**90-day targets:**
- [ ] GSC URL Inspection confirms Google-selected canonical matches declared canonical for 95%+ of priority pages
- [ ] No new canonical issues introduced after content publishing
- [ ] Faceted navigation canonical strategy documented and implemented
- [ ] Duplicate content reduction visible in GSC Coverage (fewer "Duplicate, Google chose different canonical than user")

**Reporting output:**
- Canonical Audit Report (issues by type: missing, chain, loop, conflict)
- GSC URL Inspection screenshots for key pages (Google-selected vs user-declared)
- Before/after: Count of duplicate pages indexed
