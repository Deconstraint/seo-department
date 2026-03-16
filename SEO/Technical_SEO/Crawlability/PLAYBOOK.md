# Crawlability — Technical SEO Playbook

## When to Use This

Use this playbook when:
- Onboarding a new client for a technical SEO audit
- Pages are not appearing in Google Search despite being published
- A site migration or redesign just occurred
- Organic traffic drops suddenly with no obvious content cause
- A client reports Googlebot errors in Search Console
- The site has undergone significant structural changes (URL restructuring, nav overhaul)
- You need to verify crawler access before launching any SEO campaign

---

## Step-by-Step Checklist

### 1. Baseline Crawl with Screaming Frog
- Run a full crawl of the domain: `Site Crawl > Enter URL > Start`
- Set crawl depth to unlimited; enable JavaScript rendering if the site is SPA/React/Vue
- Export: All pages, response codes, redirect chains, blocked resources
- Flag: 4xx errors, 5xx errors, redirect loops, pages returning 200 with `noindex`

### 2. Check robots.txt for Blocking Rules
- Fetch: `https://domain.com/robots.txt`
- Verify no critical paths are disallowed:
  ```
  # BAD — blocks all crawlers from entire site
  User-agent: *
  Disallow: /
  
  # BAD — blocks Googlebot from product pages
  User-agent: Googlebot
  Disallow: /products/
  ```
- Cross-reference disallowed paths against pages you want indexed
- Test specific URLs using Google Search Console > URL Inspection > Test Live URL

### 3. Audit Internal Link Structure
- Every page you want indexed must be reachable via internal links
- Use Screaming Frog: `Reports > Crawl Tree` to spot orphan pages
- Check: Are important pages buried more than 3 clicks from the homepage?
- Fix: Add internal links from high-authority pages (homepage, category pages) to orphaned content

### 4. Identify and Fix Crawl Traps
- Common traps: infinite pagination, faceted navigation generating thousands of duplicate URLs, calendar plugins generating infinite date URLs
- Example infinite pagination trap: `/products?page=1&sort=price&filter=red&filter=blue` → exponential URL combinations
- Fix with robots.txt disallow on parameterized URLs, or use `<meta name="robots" content="noindex,follow">` on facet pages
- For e-commerce: configure canonical tags on faceted pages pointing to the base category URL

### 5. Verify Crawl Budget Isn't Being Wasted
- Check Google Search Console > Settings > Crawl Stats
- Look for: high crawl rate on non-essential URLs (404s, parameterized duplicates, print versions)
- Fix: Disallow low-value URL patterns in robots.txt, consolidate duplicates with canonicals
- For large sites (10k+ pages): prioritize crawl budget by submitting an XML sitemap with only indexable URLs

### 6. Check Server Response Codes
- All key pages must return HTTP 200
- Run: `curl -I https://domain.com/target-page` to check response headers
- Redirect audit: chains longer than 2 hops waste crawl budget
  ```bash
  # Check redirect chain
  curl -L -o /dev/null -w "%{url_effective} %{http_code}\n" -s https://domain.com/old-page
  ```
- Fix chains: Update source links to point directly to the final destination URL

### 7. Test JavaScript Rendering
- Use Google Search Console > URL Inspection > View Crawled Page > Screenshot
- Compare: HTML source vs rendered output — if critical content only appears in rendered version, Googlebot may miss it
- Use Fetch & Render in GSC or run: `https://search.google.com/test/rich-results` for structured data
- If content is JS-dependent: implement SSR (Server-Side Rendering) or pre-rendering (Prerender.io, Cloudflare Workers)

### 8. Validate XML Sitemap Coverage
- Fetch: `https://domain.com/sitemap.xml` (or check robots.txt for sitemap location)
- Verify all canonical, indexable URLs are included — not blocked URLs, not redirects, not `noindex` pages
- Submit to Google Search Console: `Sitemaps > Add a new sitemap`
- Check for "Couldn't fetch" or "Has errors" status in GSC

### 9. Check for Crawl Errors in Google Search Console
- GSC > Coverage > Error tab
- Categorize: Server errors (5xx), Not found (404), Redirect errors, Submitted URL blocked by robots.txt
- Prioritize fixing: Submitted URL blocked by robots.txt (critical — you're telling Google to index a page you're also blocking)
- For 404s on linked pages: redirect to nearest relevant live page, or remove the internal link

### 10. Audit Crawl Access for Key Resources (CSS/JS/Images)
- Googlebot must be able to fetch CSS, JS, and fonts to properly render pages
- Check robots.txt — do NOT block `/static/`, `/assets/`, `/wp-content/`, or CDN paths
- Use GSC > URL Inspection > Page Resources to see what Googlebot could/couldn't load
- Fix: Remove disallow rules for critical resource directories

### 11. Log File Analysis (Advanced)
- Pull server access logs and filter for Googlebot user-agent:
  ```bash
  grep "Googlebot" /var/log/nginx/access.log | awk '{print $7}' | sort | uniq -c | sort -rn | head 50
  ```
- Identify: What is Googlebot actually crawling? Is it wasting time on `/wp-login.php`, `/search?q=`, print pages?
- Compare crawled URLs vs your target URL list — gaps = crawlability failures

### 12. Check for Hreflang Crawlability (Multilingual Sites)
- All hreflang-referenced URLs must be crawlable
- Verify alternates are not blocked in robots.txt or behind login walls
- Use Screaming Frog: `Configuration > Spider > Hreflang` to audit

---

## Common Issues and Fixes

| Issue | Symptom | Fix |
|-------|---------|-----|
| `Disallow: /` in robots.txt | Entire site de-indexed | Change to `Disallow:` (empty = allow all) |
| Redirect chains (3+ hops) | Crawl budget waste, slow indexing | Update all links to point to final destination |
| Orphan pages | Pages never indexed | Add internal links from crawled pages |
| Faceted nav crawl trap | Millions of URLs in GSC | robots.txt disallow on parameters + canonicals |
| JS-only content | GSC shows blank page renders | Implement SSR or pre-rendering |
| Blocked CSS/JS | Pages render incorrectly for Googlebot | Remove resource directory disallow rules |
| Sitemap includes non-indexable URLs | Crawl budget wasted | Regenerate sitemap with only canonical 200 URLs |
| 5xx server errors | Googlebot can't access pages | Fix server issues; check hosting logs |

---

## Tools to Use

| Tool | Purpose | URL/Command |
|------|---------|-------------|
| Screaming Frog | Full site crawl, redirect audit, orphan detection | `screaming-frog.co.uk` |
| Google Search Console | GSC Coverage, Crawl Stats, URL Inspection | `search.google.com/search-console` |
| Ahrefs Site Audit | Crawlability scoring, crawl depth analysis | `ahrefs.com/site-audit` |
| Semrush Site Audit | Crawl issues dashboard | `semrush.com` |
| curl | Manual response code checking | `curl -I https://domain.com` |
| Log analyzer (GoAccess) | Server log analysis for Googlebot patterns | `goaccess.io` |
| Robots.txt Tester | GSC built-in tool | GSC > robots.txt Tester |
| Chrome DevTools | Network tab, rendering verification | F12 > Network |

---

## How to Measure Success

**Baseline metrics (capture before fixes):**
- Number of pages crawled by Googlebot (GSC Crawl Stats)
- Number of URLs in Coverage > Valid
- Number of Coverage errors
- Average crawl depth of key pages

**30-day targets:**
- [ ] Zero "Submitted URL blocked by robots.txt" errors in GSC
- [ ] All priority pages reachable within 3 clicks of homepage
- [ ] No redirect chains longer than 2 hops
- [ ] Crawl error count reduced by ≥50%
- [ ] Sitemap submitted and showing "Success" status in GSC

**90-day targets:**
- [ ] Crawled-currently-not-indexed count trending down
- [ ] Indexing rate of new content improving (GSC Coverage > Valid trend)
- [ ] Googlebot spending crawl budget on high-value pages (log analysis)
- [ ] No new crawl traps introduced (ongoing monitoring)

**Reporting output:**
- Crawlability Audit Report (before/after table)
- GSC Coverage screenshot (baseline vs current)
- Redirect chain fix log (URLs updated, old vs new destination)
