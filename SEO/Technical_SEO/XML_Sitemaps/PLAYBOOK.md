# XML Sitemaps — Technical SEO Playbook

## When to Use This

Use this playbook when:
- Setting up a new site for the first time
- GSC shows "Sitemap not submitted" or sitemap errors
- New pages are not being discovered and indexed by Google
- After a site migration with URL structure changes
- The sitemap hasn't been updated in months (stale)
- The site has more than 500 pages (requires sitemap index management)
- Multilingual/hreflang implementation needs validation
- You want to prioritize specific content types for faster indexing

---

## Step-by-Step Checklist

### 1. Locate and Fetch the Existing Sitemap
- Common locations:
  ```
  https://domain.com/sitemap.xml
  https://domain.com/sitemap_index.xml
  https://domain.com/wp-sitemap.xml       (WordPress default)
  https://domain.com/sitemap.xml.gz       (compressed)
  ```
- Also check robots.txt for `Sitemap:` directive:
  ```bash
  curl https://domain.com/robots.txt | grep -i sitemap
  ```
- If no sitemap exists, proceed to step 3 to generate one

### 2. Validate Sitemap Structure and Syntax
- Valid XML sitemap format:
  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
  <urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
    <url>
      <loc>https://www.domain.com/page/</loc>
      <lastmod>2025-03-01</lastmod>
      <changefreq>monthly</changefreq>
      <priority>0.8</priority>
    </url>
  </urlset>
  ```
- Validate using: `https://www.xml-sitemaps.com/validate-xml-sitemap.html`
- Common errors: encoding issues, unclosed tags, non-UTF-8 characters, relative URLs instead of absolute

### 3. Audit What's IN the Sitemap (Should Be vs Should NOT Be)

**Should be in sitemap:**
- All canonical, indexable, 200-status URLs
- Paginated pages (if each has unique content — use `rel=next/prev` or just list them)
- Translated/hreflang alternate URLs

**Should NOT be in sitemap:**
- `noindex` pages (sending mixed signals to Google)
- Redirected URLs (301/302 destinations only, not the redirect source)
- 404 pages
- Parameterized URL duplicates (`?sort=price&color=red`)
- Login-required pages
- Thin/auto-generated pages (tag archives, author pages on non-blog sites)

Use Screaming Frog: `Sitemaps > Sitemap Analysis` to identify invalid entries.

### 4. Ensure All Indexable Pages Are Listed
- Export all pages from Screaming Frog (HTTP 200, no noindex)
- Export all URLs from current sitemap
- Compare lists — pages in crawl but not sitemap = indexing opportunity missed
- Fix: Regenerate sitemap or manually add missing URLs

### 5. Use Sitemap Index for Large Sites (500+ pages)
- A single sitemap file supports max 50,000 URLs and 50MB uncompressed
- For larger sites, use a sitemap index:
  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
  <sitemapindex xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
    <sitemap>
      <loc>https://www.domain.com/sitemap-pages.xml</loc>
      <lastmod>2025-03-01</lastmod>
    </sitemap>
    <sitemap>
      <loc>https://www.domain.com/sitemap-posts.xml</loc>
      <lastmod>2025-03-01</lastmod>
    </sitemap>
    <sitemap>
      <loc>https://www.domain.com/sitemap-products.xml</loc>
      <lastmod>2025-03-01</lastmod>
    </sitemap>
  </sitemapindex>
  ```
- Break sitemaps by content type (pages, posts, products, images, news, video)

### 6. Set Accurate `<lastmod>` Dates
- `<lastmod>` should reflect the actual date the page content was last changed
- Do NOT use today's date for all pages — this is flagged as spam/manipulation by Google
- Format: `YYYY-MM-DD` or full ISO 8601: `2025-03-01T14:32:00+00:00`
- For WordPress: Yoast and RankMath auto-populate `<lastmod>` from post modified date — verify in plugin settings

### 7. Add Sitemap Directive to robots.txt
- Every sitemap must be declared in robots.txt:
  ```
  Sitemap: https://www.domain.com/sitemap.xml
  Sitemap: https://www.domain.com/sitemap-index.xml
  ```
- This ensures all crawlers (Google, Bing, etc.) can discover it automatically

### 8. Submit Sitemap to Google Search Console
- GSC > Sitemaps > Enter sitemap URL > Submit
- Verify status shows "Success" not "Couldn't fetch" or "Has errors"
- If errors: click through to see specific URL-level issues
- Note: GSC will show "Submitted" vs "Indexed" counts — large gap = indexability issues (not sitemap issues)

### 9. Submit Sitemap to Bing Webmaster Tools
- `https://www.bing.com/webmasters`
- Sitemaps > Submit sitemap URL
- Bing also supports automatic discovery via robots.txt `Sitemap:` directive

### 10. Implement Image Sitemaps (if site is image-heavy)
- For photography, e-commerce, or media sites, image sitemaps help Google index images
  ```xml
  <url>
    <loc>https://www.domain.com/product/widget/</loc>
    <image:image>
      <image:loc>https://www.domain.com/images/widget-main.jpg</image:loc>
      <image:title>Blue Widget Product Photo</image:title>
    </image:image>
  </url>
  ```
- Namespace required: `xmlns:image="http://www.google.com/schemas/sitemap-image/1.1"`

### 11. Implement Video Sitemaps (if site has video content)
- Required for YouTube embeds or hosted videos you want indexed:
  ```xml
  <video:video>
    <video:thumbnail_loc>https://www.domain.com/thumbs/video1.jpg</video:thumbnail_loc>
    <video:title>How to Install Widget</video:title>
    <video:description>Step by step guide...</video:description>
    <video:content_loc>https://www.domain.com/videos/widget-install.mp4</video:content_loc>
  </video:video>
  ```

### 12. Set Up Automated Sitemap Regeneration
- Sitemaps should auto-update when new content is published
- WordPress: Yoast SEO, RankMath, or All in One SEO auto-regenerate on publish
- Custom/static sites: Add sitemap generation to CI/CD pipeline or deploy hook
- Verify: Publish a test page, wait 5 minutes, confirm new URL appears in sitemap

---

## Common Issues and Fixes

| Issue | Symptom | Fix |
|-------|---------|-----|
| noindex pages in sitemap | Mixed signals to Google; wasted crawl budget | Regenerate sitemap excluding noindex pages |
| Redirected URLs in sitemap | Google follows redirect, notes inconsistency | Replace redirect URLs with final destination URLs |
| Sitemap not in robots.txt | Slower discovery | Add `Sitemap:` directive to robots.txt |
| Stale `<lastmod>` or fake dates | Google ignores lastmod signals | Use real modification dates from CMS |
| Sitemap returns 404 | GSC "Couldn't fetch" error | Fix server config or regenerate at correct path |
| Missing high-value pages | Slower indexing | Add missing URLs to sitemap |
| Single file exceeds 50,000 URLs | Sitemap parse error | Split into sitemap index with multiple files |
| Non-canonical URLs listed | Duplicate indexing signals | Only include canonical URLs in sitemap |

---

## Tools to Use

| Tool | Purpose |
|------|---------|
| Google Search Console | Sitemap submission, error reporting, indexed count |
| Screaming Frog | Sitemap analysis, URL validation, audit vs crawl comparison |
| XML Sitemap Validator | Syntax validation (`xml-sitemaps.com/validate-xml-sitemap.html`) |
| Yoast SEO / RankMath | WordPress sitemap generation |
| Screaming Frog Sitemap Generator | Generate sitemaps for any site |
| Bing Webmaster Tools | Secondary sitemap submission |
| curl | Manual fetch/validation of sitemap XML |

---

## How to Measure Success

**Baseline metrics:**
- GSC Sitemaps: Submitted count vs Indexed count (and gap %)
- Number of sitemap errors in GSC
- Number of sitemap URLs that are noindex or redirect

**30-day targets:**
- [ ] Sitemap submitted to GSC showing "Success" status
- [ ] Zero noindex or redirect URLs in sitemap
- [ ] Sitemap declared in robots.txt
- [ ] Sitemap auto-regenerates within 1 hour of new content publishing
- [ ] Submitted vs Indexed gap documented (baseline established)

**90-day targets:**
- [ ] GSC Sitemaps "Indexed" count approaching "Submitted" count (gap ≤ 20%)
- [ ] New pages appearing in GSC Coverage within 7 days of publish
- [ ] Sitemap index structure in place for sites with 500+ pages
- [ ] Image/video sitemaps live for media-heavy content

**Reporting output:**
- Sitemap audit summary (issues found, URLs removed/added)
- GSC Sitemaps screenshot (submitted vs indexed before/after)
- Sitemap structure diagram (for sitemap index implementations)
