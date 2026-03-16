# Indexability — Technical SEO Playbook

## When to Use This

Use this playbook when:
- Pages are crawled but not appearing in Google search results
- GSC Coverage shows high "Crawled - currently not indexed" or "Discovered - currently not indexed" counts
- A client says "I can't find my pages on Google"
- After a site migration where canonical structure changed
- Pages exist with `noindex` that shouldn't have it
- Duplicate content is suspected across the site
- A penalty or manual action may have de-indexed pages
- You need to verify that key landing pages are indexable before a campaign launch

---

## Step-by-Step Checklist

### 1. Audit Meta Robots Tags Across All Pages
- Use Screaming Frog: `Configuration > Spider > Extraction > Add custom extraction`
- XPath for meta robots: `//meta[@name='robots']/@content`
- Export all pages and filter for values: `noindex`, `noindex,nofollow`, `none`
- Fix: Remove `noindex` from any page that should be indexed
  ```html
  <!-- REMOVE THIS from pages you want indexed -->
  <meta name="robots" content="noindex, nofollow">
  
  <!-- CORRECT for indexable pages -->
  <meta name="robots" content="index, follow">
  <!-- OR simply omit the tag — default is index,follow -->
  ```

### 2. Check X-Robots-Tag HTTP Headers
- Some CMS platforms set `X-Robots-Tag: noindex` in HTTP headers (staging environments, password-protected pages)
- Check with curl:
  ```bash
  curl -I https://domain.com/target-page | grep -i x-robots
  ```
- Common offender: WordPress staging sites pushed to production with staging `noindex` header still active
- Fix: Remove the header in server config (nginx/Apache) or plugin settings (Yoast, RankMath)

### 3. Verify Google's Index Status via URL Inspection
- GSC > URL Inspection > Enter URL > Request Indexing (if needed)
- Check "Coverage" section: Is it indexed? What's the verdict?
- For batch checking: `site:domain.com/specific-page` in Google Search
- Note: `site:` operator is unreliable for absolute counts; use GSC Coverage for authoritative data

### 4. Audit Canonical Tags for Correctness
- Every page must have a self-referencing canonical (or correctly point to the preferred version)
  ```html
  <!-- Self-referencing canonical (preferred) -->
  <link rel="canonical" href="https://www.domain.com/page-slug/" />
  
  <!-- Pointing to preferred version (e.g., removing trailing slash variation) -->
  <link rel="canonical" href="https://www.domain.com/page-slug" />
  ```
- Use Screaming Frog > Canonicals tab to find:
  - Pages with no canonical
  - Pages with canonicals pointing to different domains
  - Canonical chains (A → B → C, should be A → C)
  - Canonicals pointing to noindex or 404 pages

### 5. Check for Duplicate Content Issues
- Identify thin/duplicate pages using Screaming Frog: `Content > Duplicate Content`
- Common duplicate scenarios:
  - `http://` vs `https://` both accessible
  - `www` vs `non-www` both accessible
  - Trailing slash vs non-trailing slash (`/page` vs `/page/`)
  - URL parameters (`?utm_source=email` creating duplicate indexable URLs)
- Fix: Pick one canonical version, redirect all others permanently (301), and set canonical tags
  ```nginx
  # nginx: redirect www to non-www
  server {
    server_name www.domain.com;
    return 301 https://domain.com$request_uri;
  }
  ```

### 6. Diagnose "Crawled - Currently Not Indexed"
- This status means Google chose not to index the page — usually due to thin content, duplication, or low quality signals
- Check the page for:
  - Word count under 300 words with no unique value
  - Near-duplicate of another page on the site
  - Thin product/category pages with boilerplate text
  - Very slow page speed (Googlebot deprioritizes slow pages)
- Fix: Improve content depth, consolidate thin pages, add unique value (original data, structured FAQ, etc.)

### 7. Audit "Discovered - Currently Not Indexed"
- Google knows about the URL (from sitemap or links) but hasn't crawled it yet
- Common causes: low crawl budget, poor internal linking, server slowness
- Fix:
  1. Add strong internal links from high-authority pages
  2. Include URL in XML sitemap
  3. Use GSC URL Inspection > Request Indexing for high-priority pages (max ~10/day)
  4. Improve page speed to make crawling more efficient

### 8. Check for Soft 404s
- Pages returning HTTP 200 but displaying "Page not found" or empty content
- Googlebot treats these as real pages and wastes crawl budget
- Detect: GSC > Coverage > Soft 404
- Fix: Serve proper 404 HTTP status for missing pages, or redirect to a relevant live page
  ```php
  // WordPress — send real 404 header
  header("HTTP/1.0 404 Not Found");
  ```

### 9. Verify Noindex Not Set in WordPress/CMS Settings
- WordPress: Settings > Reading > "Discourage search engines from indexing this site" — this sets sitewide noindex
- This is the #1 staging-site-pushed-to-production mistake
- Yoast SEO: SEO > Search Appearance > set "Yes, show in search results" for all post types
- RankMath: General Settings > Robots Meta > ensure noindex is NOT checked globally

### 10. Check for Manual Actions or Penalties
- GSC > Security & Manual Actions > Manual Actions
- Types: Thin content with little or no added value, Cloaking, Unnatural links
- Fix: Follow Google's specific guidance per penalty type; file a reconsideration request after fixing

### 11. Evaluate Content Quality Signals
- Google's Helpful Content System may suppress indexing of low-quality content
- Audit each key page for:
  - Does it have a clear, unique purpose?
  - Does it answer the user's question better than competitors?
  - Does it have adequate E-E-A-T signals (author, date, sources)?
- Use: `site:domain.com` in Google + compare count to actual page count — large discrepancy = indexing suppression

### 12. Validate Structured Data (Indexing Aid)
- Well-structured data improves Google's ability to understand and index content correctly
- Test: `https://search.google.com/test/rich-results`
- Ensure no structured data errors that could confuse Googlebot's interpretation of page type

---

## Common Issues and Fixes

| Issue | Root Cause | Fix |
|-------|-----------|-----|
| `noindex` on live pages | Staging config pushed to prod | Remove meta robots noindex tag / HTTP header |
| "Crawled - currently not indexed" | Thin/duplicate content | Improve content depth, merge thin pages |
| Canonical pointing to wrong URL | CMS misconfiguration | Correct canonical to self-referencing or preferred URL |
| Duplicate pages all indexed | Missing redirect/canonical | 301 redirect all variants to canonical; add canonical tag |
| Soft 404s | CMS returns 200 for missing pages | Serve real 404 header or redirect to live page |
| `www` and `non-www` both indexed | Missing redirect | 301 all traffic to preferred domain version |
| Sitewide noindex (WordPress) | Search engine discourage checkbox | Uncheck in WordPress Reading Settings |
| Manual action | Spam/thin/cloaking | Fix root cause, submit reconsideration request |

---

## Tools to Use

| Tool | Purpose |
|------|---------|
| Google Search Console | Coverage report, URL Inspection, Manual Actions |
| Screaming Frog | Meta robots extraction, canonical audit, duplicate detection |
| Ahrefs Site Audit | Indexability health score, noindex/canonical issues |
| curl | Check X-Robots-Tag headers manually |
| Google Search (`site:`) | Spot-check index status of specific pages |
| Rich Results Test | Structured data validation |
| Semrush Site Audit | Duplicate content detection |

---

## How to Measure Success

**Baseline metrics (capture day 1):**
- GSC Coverage: count of Valid, Excluded, Error, Warning URLs
- Count of "Crawled - currently not indexed" URLs
- Count of "Discovered - currently not indexed" URLs
- Number of pages with unintended noindex

**30-day targets:**
- [ ] Zero pages with unintended `noindex` or blocking `X-Robots-Tag`
- [ ] All canonical tags self-referencing or pointing to correct preferred URL
- [ ] "Crawled - currently not indexed" count reduced by ≥30%
- [ ] All priority landing pages confirmed indexed via GSC URL Inspection
- [ ] No active Manual Actions

**90-day targets:**
- [ ] GSC Valid URL count matches expected indexable page count (within 10%)
- [ ] "Discovered - currently not indexed" queue cleared for all priority URLs
- [ ] Zero soft 404s in Coverage report
- [ ] Content quality improvements reflected in indexing rate for new pages

**Reporting output:**
- Indexability Audit Report (before/after counts per GSC Coverage category)
- Noindex fix log (URLs corrected, what was removed)
- Canonical audit summary (errors found and resolved)
