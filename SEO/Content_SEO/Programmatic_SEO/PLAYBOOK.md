# Programmatic SEO — Playbook

> **Purpose:** Build, launch, and scale hundreds or thousands of SEO-optimized pages from structured data using programmatic templates — without writing each page manually.

---

## When to Use This Playbook

- Client has a large dataset that maps to searchable queries (locations, products, professions, comparisons, etc.)
- Client needs to scale to hundreds of pages quickly
- Target keywords follow a clear, repeatable pattern (e.g., "[service] in [city]", "[X] vs [Y]", "best [X] for [use case]")
- Client is in a marketplace, SaaS, directory, or multi-location business model
- SEO strategy requires capturing long-tail keyword volume at scale
- Manual content creation is cost-prohibitive for the number of pages needed

---

## Step-by-Step Process

### Step 1: Identify the Programmatic Pattern

1. Research what keyword patterns have consistent search volume in the client's niche
2. Common patterns to look for:
   - `[service] in [city]` — local service businesses
   - `[tool] for [use case]` — SaaS and software
   - `best [product] for [persona]` — affiliate, ecommerce
   - `[job title] salary in [city]` — HR, recruiting platforms
   - `[X] vs [Y]` — comparison pages
   - `[industry] [template/calculator/tool]` — utility pages
3. Validate pattern volume: in Ahrefs/Semrush, check if pattern produces consistent impressions across variations
4. Set minimum search volume threshold per page (typically ≥ 50 searches/month to justify page creation)
5. Document the pattern with a clear naming convention: `{modifier} + {variable}`

### Step 2: Build the Data Set

1. Identify the variable data source:
   - Internal database (CRM, product catalog)
   - Public dataset (census data, job boards, Wikipedia exports)
   - Scraped/purchased data (cities, professions, use cases, etc.)
2. Normalize and clean the data:
   - Remove duplicates
   - Standardize formatting (e.g., "New York City" vs "NYC" vs "New York, NY")
   - Add supporting data fields that will enrich the page content
3. Structure data in spreadsheet/JSON/CSV with all required template variables
4. Example columns: `city`, `state`, `population`, `avg_cost`, `num_providers`, `lat`, `long`
5. QA data for accuracy — bad data = bad pages = Google penalties

### Step 3: Template Design

1. Create the master page template with placeholder variables:
   - `{city}` `{service}` `{stat_1}` `{comparison_name}` etc.
2. Template must include:
   - Unique H1 for each page variation
   - Unique meta title and meta description (use variable injection)
   - At least 1–2 sections of unique content per page (beyond template copy)
   - Dynamic stats, data tables, or local facts to differentiate pages
3. Write the "evergreen wrapper" — the structural body copy that works for all variations
4. Mark sections as: [STATIC] (same across all pages) vs. [DYNAMIC] (unique per page)
5. Design for at least 400–800 words of useful, non-duplicated content per page

### Step 4: Uniqueness Strategy (Critical)

> Google penalizes thin, duplicated programmatic pages. Every page must have unique value.

1. Pull in unique data for each page (stats, pricing, population, demand index)
2. Include a unique FAQ section per variable (e.g., "How much does [service] cost in [city]?")
3. Add a dynamically-generated table with local data (providers, comparisons, pricing ranges)
4. If possible, include user-generated content, reviews, or ratings per variation
5. Minimum uniqueness threshold: at least 30% of content should be unique per page

### Step 5: Technical Infrastructure Setup

1. Choose implementation approach:
   - **CMS-based** (WordPress with ACF/custom post types, Webflow CMS, Contentful)
   - **Headless/SSG** (Next.js, Gatsby, Astro with JSON/Markdown data)
   - **Custom scripting** (Python + templating engine like Jinja2)
2. Create URL structure:
   - Pattern: `/[parent-slug]/[variable-slug]`
   - Example: `/seo-services/denver-co`
3. Build sitemap generation logic (auto-generate XML sitemap as pages are created)
4. Set up pagination if needed for very large page sets (avoid paginating unless >1,000 pages)
5. Configure robots.txt to allow crawling of new URL patterns

### Step 6: Internal Linking at Scale

1. Create a hub/index page for each variable group:
   - `/seo-services/` → links to all city pages
   - Hub page targets the head term; individual pages target long-tail
2. Implement automated cross-linking within similar variable groups:
   - On `/seo-services/denver-co` → link to `/seo-services/boulder-co` and `/seo-services/fort-collins-co`
3. Link hub pages from the main navigation or footer
4. Add breadcrumb navigation with structured data
5. On hub page: alphabetical or grouped listing of all child pages with anchor links

### Step 7: Content QA & Thin Content Prevention

1. Run spot-check on 10% of generated pages before mass publishing
2. Checklist per page:
   - [ ] Unique H1
   - [ ] Unique meta title and description
   - [ ] Page has ≥ 400 words
   - [ ] Dynamic content loaded correctly (no empty variables like "{city}")
   - [ ] At least one unique data point or stat
   - [ ] Internal links functioning
3. Use Screaming Frog to crawl and flag: duplicate titles, thin content, broken links
4. Check for template rendering errors (empty fields, fallback values, encoding issues)

### Step 8: Staged Rollout

1. **Phase 1:** Launch 50–100 pages (highest-volume variables first)
2. Monitor indexing rate and ranking performance for 4–6 weeks
3. Check Google Search Console for manual actions or crawl errors
4. **Phase 2:** If Phase 1 performs, expand to full dataset
5. Submit sitemap to GSC after each phase

### Step 9: Indexation Management

1. Submit XML sitemap to Google Search Console
2. Monitor Coverage report in GSC for "Discovered but not indexed" issues
3. If crawl rate is slow, build internal PageRank to new pages from high-authority existing pages
4. For large sites (1,000+ pages): prioritize highest-value pages in sitemap (use `<priority>`)
5. Consider using IndexNow API for faster indexation of new pages

### Step 10: Performance Monitoring & Iteration

1. Track top 20 pages by impressions monthly in GSC
2. Identify patterns: which variable groups rank best? (cities with higher population? Specific use cases?)
3. Expand content depth on top-performing pages (add more unique sections, testimonials, data)
4. Prune or redirect pages with 0 impressions after 90 days (noindex or consolidate)
5. Test content variations (A/B on template sections) to optimize performance across the board

---

## Programmatic Page Template Example (Location Pages)

```markdown
---
title: "[Service] in [City], [State] | [Brand]"
description: "Looking for [service] in [city]? [Brand] helps businesses in [city] 
  achieve [outcome]. Get a free consultation today."
url: /[service-slug]/[city-slug]-[state-code]
---

# [Service] in [City], [State]

[Brand] provides expert [service] to businesses across [city]. Whether you're a 
[industry-1] or [industry-2], our [service] solutions drive measurable results.

## Why [City] Businesses Choose [Brand]

[City] has a growing market of [population-estimate] residents and [num_businesses] 
active businesses. Competition for online visibility is [competition_level], making 
[service] a critical investment for local brands.

## Our [Service] Services in [City]

### [Service Category 1]
[Description of service offering, localized where possible]

### [Service Category 2]
[Description]

### [Service Category 3]
[Description]

## [Service] Pricing in [City]

| Service Tier | Price Range | Includes |
|---|---|---|
| Starter | $[min]–$[mid] | [features] |
| Growth | $[mid]–$[max] | [features] |
| Enterprise | Custom | [features] |

*Pricing varies based on project scope. [avg_market_note]*

## Frequently Asked Questions

### How much does [service] cost in [city]?
[Dynamic answer using city/service data]

### How long does [service] take in [city]?
[Answer]

### What [service] results can businesses in [city] expect?
[Answer with local context]

## Get Started with [Service] in [City]

[CTA section with form or phone number]
```

---

## Data Structure Template (CSV/JSON)

```
Fields required per page:
- city (string)
- state (string)
- state_code (string, 2-letter)
- city_slug (string, URL-safe)
- population (integer)
- num_businesses (integer or estimate)
- competition_level (string: low/medium/high)
- avg_price_low (integer)
- avg_price_mid (integer)  
- avg_price_high (integer)
- avg_market_note (string, unique sentence)
- industry_1, industry_2 (string, common local industries)
- unique_fact (string, 1 sentence about the local market)
```

---

## Building Topical Authority at Scale

- Each programmatic hub page = pillar in the topical cluster
- Blog content supports programmatic pages: "How to choose [service] in [state]" → links to all city pages
- Interlink between programmatic pages using "nearby cities" or "related comparisons" sections
- Use breadcrumbs: `Home > [Service] > [State] > [City]`

---

## Tools & Workflow

| Tool | Purpose |
|---|---|
| Ahrefs / Semrush | Pattern validation, volume analysis |
| Python / Node.js | Data transformation, page generation scripts |
| Next.js / Gatsby / Astro | Headless SSG for scalable page rendering |
| Contentful / Sanity | Headless CMS for data-driven templates |
| Screaming Frog | Post-launch crawl and QA |
| Google Search Console | Indexation monitoring, coverage report |
| Google Sheets + GPT | Data enrichment, unique content generation |
| Airtable | Dataset management at scale |

---

## Performance Metrics & KPIs

| Metric | Target | Check At |
|---|---|---|
| Pages indexed / pages submitted | ≥ 80% | 30–60 days |
| Total impressions (GSC) | Growing week over week | Monthly |
| Top-performing pages | Identify top 20% | 60 days |
| Thin content rate | < 5% of pages | 30 days post-launch |
| Manual action in GSC | Zero | Ongoing |
| Pages with clicks | Growing set | Monthly |
| Average position for pattern keywords | < 30 within 90 days | 90 days |

---

## Common Mistakes to Avoid

- Publishing pages with no unique content beyond template copy (thin content)
- Generating pages for keywords with zero real search volume
- No hub/index page connecting all programmatic pages
- Missing or broken variable injection (rendering `{city}` literally)
- Launching all pages at once without a phased rollout and monitoring
- Ignoring GSC Coverage report after launch
- Not building internal links from existing high-authority pages to new programmatic pages
- Duplicate title tags across pages (must be unique per page)
