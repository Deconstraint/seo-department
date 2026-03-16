# Robots.txt — Technical SEO Playbook

## When to Use This

Use this playbook when:
- Conducting a new client technical audit
- Pages that should be indexed are not appearing in Google
- GSC shows "Blocked by robots.txt" errors in Coverage
- After a site migration or platform change (robots.txt may have reset)
- A developer deployed a staging `noindex` robots.txt to production
- You need to block specific sections from crawlers (admin panels, staging paths, duplicate parameter URLs)
- A competitor appears to be scraping your client's site (block their bot)

---

## Step-by-Step Checklist

### 1. Fetch and Review Current robots.txt
```bash
curl https://domain.com/robots.txt
```
- Must return HTTP 200. If 404, Google assumes the file doesn't exist and crawls everything (mostly fine, but you want control)
- If 5xx, Google assumes blocked and may stop crawling the site — critical error
- Review every rule against your list of pages that should be indexed

### 2. Understand robots.txt Syntax Precisely
Full syntax reference:
```
# Comment lines start with hash

User-agent: *          # Applies to all crawlers
User-agent: Googlebot  # Applies only to Googlebot
User-agent: Bingbot    # Applies only to Bing

Disallow: /admin/      # Block this path and everything under it
Disallow: /private     # Blocks /private and /private-page (substring match)
Allow: /public/        # Explicitly allow (overrides broader disallow)

Disallow:              # Empty = allow everything (this is the default)
Disallow: /            # Block EVERYTHING — nuclear option

Crawl-delay: 10        # Wait 10 seconds between requests (Bing/others only; Google ignores this)

Sitemap: https://www.domain.com/sitemap.xml
```

### 3. Verify the Critical Production Rule
The single most dangerous robots.txt line:
```
# DANGER — blocks all crawlers from everything
User-agent: *
Disallow: /
```
This is often set on staging environments and accidentally pushed to production.
- Check immediately on any new client site
- If found, confirm this is NOT the live/production site before changing

### 4. Audit Every Disallow Rule Intentionality
For each `Disallow:` line, answer:
- What pages does this block? (use GSC robots.txt tester to check specific URLs)
- Should those pages be crawlable?
- Is this block still needed?

Common legitimate disallows:
```
Disallow: /wp-admin/          # WordPress admin panel
Disallow: /wp-login.php       # WordPress login
Disallow: /cart/              # E-commerce cart (thin, no SEO value)
Disallow: /checkout/          # Checkout flow
Disallow: /account/           # User account pages
Disallow: /search/            # Internal search results (duplicate content)
Disallow: /*?s=               # WordPress search parameter
Disallow: /*?replytocom=      # WordPress comment reply parameters
```

### 5. Handle URL Parameters That Generate Duplicates
Block parameter-based duplicate URLs:
```
# Block faceted navigation parameters
Disallow: /*?color=
Disallow: /*?size=
Disallow: /*?sort=
Disallow: /*?page=            # Only if paginated pages have no unique SEO value
```
**Caution:** Use `Allow:` rules to punch exceptions if needed:
```
Disallow: /*?
Allow: /*?lang=               # Keep language parameter accessible
```

### 6. Protect Non-SEO Paths from Crawl Waste
These paths waste crawl budget and should typically be disallowed:
```
Disallow: /cdn-cgi/           # Cloudflare internal paths
Disallow: /wp-json/           # WordPress REST API (no SEO value)
Disallow: /xmlrpc.php         # WordPress XML-RPC
Disallow: /trackback/         # WordPress trackbacks
Disallow: /feed/              # RSS feeds (unless you want them indexed)
Disallow: /tag/               # Tag archives (if thin — evaluate per site)
Disallow: /author/            # Author archives (if thin)
Disallow: /print/             # Print versions of pages
Disallow: /*.pdf$             # PDFs (if you don't want them in search)
```

### 7. Do NOT Block CSS, JavaScript, or Image Resources
Google needs to render pages to understand them. Never block:
```
# WRONG — breaks Googlebot's ability to render pages
Disallow: /wp-content/themes/
Disallow: /wp-content/plugins/
Disallow: /assets/
Disallow: /static/
```
If these are currently blocked, remove those rules immediately.

### 8. Validate the Sitemap Directive
Every robots.txt should declare sitemaps:
```
Sitemap: https://www.domain.com/sitemap.xml
Sitemap: https://www.domain.com/sitemap-index.xml
```
- Use full absolute URL including protocol
- List all sitemaps if multiple exist
- Bing, Google, and others use this for discovery

### 9. Test Every Rule with GSC robots.txt Tester
- GSC > Settings > robots.txt Tester (or `search.google.com/search-console` > robots.txt tester link)
- Test specific URLs you care about:
  - Key landing pages → should return "Allowed"
  - Admin paths → should return "Blocked"
  - Product/category pages → should return "Allowed"
- Do this for both `Googlebot` and `*` rules

### 10. Handle Multiple User-Agent Blocks Correctly
Robots.txt processes rules in order. A URL is blocked if any applicable rule blocks it.
```
# Correct structure — separate blocks per agent
User-agent: Googlebot
Disallow: /no-google/

User-agent: Bingbot
Disallow: /no-bing/

User-agent: *
Disallow: /admin/
Disallow: /cart/
```
**Note:** You CANNOT combine user-agents with shared rules like this:
```
# WRONG — this only applies to user-agent "Bingbot"
User-agent: Googlebot
User-agent: Bingbot
Disallow: /private/
```
Each `User-agent:` line starts a new block. Rules apply to the LAST declared agent before them.

### 11. Block Harmful or Scraper Bots (Optional but Recommended)
```
# Block known bad bots / scrapers
User-agent: AhrefsBot
Disallow: /

User-agent: SemrushBot
Disallow: /

User-agent: MJ12bot
Disallow: /

User-agent: DotBot
Disallow: /
```
**Note:** Malicious bots don't respect robots.txt. This mainly blocks polite crawlers to reduce server load.

### 12. Set Up robots.txt Monitoring
- Any change to robots.txt can accidentally de-index large site sections
- Monitor via GSC > Coverage > "Blocked by robots.txt" count (set up email alerts)
- Add robots.txt to version control — every change should be a tracked commit
- Consider using a robots.txt staging test before deploying changes:
  ```bash
  # Test robots.txt locally before deploying
  curl -s https://staging.domain.com/robots.txt | diff - robots.txt
  ```

---

## Complete Production-Ready robots.txt Template

```
# robots.txt for domain.com
# Last updated: 2025-03-01

User-agent: *
# Admin and auth paths
Disallow: /wp-admin/
Disallow: /wp-login.php
Disallow: /wp-json/
Disallow: /xmlrpc.php

# Duplicate/thin content paths
Disallow: /search/
Disallow: /*?s=
Disallow: /cart/
Disallow: /checkout/
Disallow: /account/
Disallow: /feed/
Disallow: /trackback/

# Faceted navigation (e-commerce)
# Disallow: /*?color=
# Disallow: /*?size=
# (uncomment if applicable)

# Allow everything else
Allow: /

# Sitemaps
Sitemap: https://www.domain.com/sitemap.xml
```

---

## Common Issues and Fixes

| Issue | Symptom | Fix |
|-------|---------|-----|
| `Disallow: /` for all agents | Entire site de-indexed | Change to `Disallow:` (empty) or remove line |
| Blocks CSS/JS resources | Pages render incorrectly for Googlebot | Remove disallow rules for resource directories |
| Missing Sitemap directive | Slower sitemap discovery | Add `Sitemap:` line with full URL |
| Overly broad parameter blocking | Blocks legitimate pages | Use more specific parameter patterns |
| Duplicate user-agent blocks with wrong order | Rules apply to wrong bot | Fix block structure (one agent per block) |
| Staging robots.txt on production | Site de-indexed | Replace with production-appropriate rules |
| robots.txt returning 5xx | Googlebot stops crawling | Fix server error; ensure file is accessible |

---

## Tools to Use

| Tool | Purpose |
|------|---------|
| Google Search Console | robots.txt tester, Coverage > Blocked by robots.txt |
| Screaming Frog | Crawl with robots.txt disabled to find blocked pages |
| curl | Manual robots.txt fetch and inspection |
| robots.txt Validator | `https://en.ryte.com/free-tools/robots-txt/` |
| Bing Webmaster Tools | Bing-specific robots.txt tester |
| Google's robots.txt documentation | `https://developers.google.com/search/docs/crawling-indexing/robots/intro` |

---

## How to Measure Success

**Baseline metrics:**
- GSC Coverage: "Blocked by robots.txt" URL count
- GSC Coverage: "Submitted URL blocked by robots.txt" count (critical — these are in your sitemap AND blocked)
- Number of disallow rules (document all)

**30-day targets:**
- [ ] Zero "Submitted URL blocked by robots.txt" in GSC (absolute priority)
- [ ] All CSS/JS/image resource paths confirmed accessible to Googlebot
- [ ] Sitemap directive present in robots.txt
- [ ] robots.txt in version control with change log
- [ ] All disallow rules reviewed and intentional

**90-day targets:**
- [ ] "Blocked by robots.txt" count reflects only intentionally blocked URLs
- [ ] No new accidental blocks introduced after site updates
- [ ] robots.txt monitoring alert in place via GSC or third-party tool
- [ ] Crawl budget waste from parameterized URLs measurably reduced

**Reporting output:**
- robots.txt audit document (before/after rules, rationale for each)
- GSC Coverage "Blocked by robots.txt" screenshot (baseline vs current)
- Version-controlled robots.txt with change log
