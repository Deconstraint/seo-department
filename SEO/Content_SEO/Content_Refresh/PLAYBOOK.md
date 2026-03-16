# Content Refresh — SEO Playbook

> **Purpose:** Systematically identify, prioritize, and revitalize underperforming or decaying content to recover lost rankings, improve click-through rates, and compound existing SEO equity instead of starting from scratch.

---

## When to Use This Playbook

- Client has an existing blog with 20+ posts but declining or plateau traffic
- Individual pages that previously ranked have dropped 5+ positions
- Content is accurate but outdated (statistics, tools, methods referenced are old)
- Pages getting impressions in GSC but low clicks (CTR optimization needed)
- Pages ranked position 5–20 that need a push to break into top 3
- Post-algorithm update recovery (Google core updates often punish thin/outdated content)
- Client wants better ROI from existing content before investing in new content
- Content audit reveals pages with high bounce rate or low dwell time

---

## Core Principle

**Content refresh is almost always higher ROI than publishing new content.** An existing page already has:
- Backlinks pointing to it
- Crawl history and indexing
- Historical ranking signals
- Internal link equity

Refreshing is rebuilding on an existing foundation — far more efficient than starting from zero.

---

## Step-by-Step Process

### Step 1: Content Audit — Build the Full Inventory

1. Pull all indexed URLs from the site using:
   - Screaming Frog crawl (export all URLs)
   - Google Search Console (Performance report → filter by page)
   - Ahrefs Site Audit (Pages section)
2. Export to a spreadsheet with columns:
   - URL
   - Page title
   - Publish date
   - Last modified date
   - Impressions (last 90 days from GSC)
   - Clicks (last 90 days from GSC)
   - Avg. position (GSC)
   - CTR (GSC)
   - Organic sessions (GA4)
   - Bounce rate / Engagement rate (GA4)
   - Backlinks (Ahrefs)
   - Word count
3. This becomes your master content audit spreadsheet

### Step 2: Categorize Each Page

Assign each page to one of these categories:

| Category | Criteria | Action |
|---|---|---|
| **Keep & Promote** | Ranking top 3, growing traffic | Add internal links, promote via outreach |
| **Refresh** | Ranking 4–20, has backlinks, traffic declining | Full content refresh (this playbook) |
| **Optimize** | Getting impressions, low CTR | Title/meta rewrite only |
| **Merge** | Two pages covering same topic, both underperforming | Consolidate into one stronger page |
| **Redirect & Kill** | Zero impressions, no backlinks, low value | 301 redirect to relevant page |
| **Delete** | Zero impressions, zero backlinks, thin/irrelevant content | Remove and redirect to category/home |

### Step 3: Prioritize the Refresh Queue

Score each "Refresh" candidate 1–10 on each dimension:
- **Traffic potential:** How much volume does the primary keyword have?
- **Current momentum:** Is it getting ANY impressions? (easier to accelerate)
- **Backlink value:** Does it have backlinks that are anchoring authority here?
- **Business relevance:** Does this topic align with client's core services/goals?
- **Effort to refresh:** Is this a minor update or full rewrite?

Prioritize: High traffic potential + existing backlinks + business relevance = highest priority refresh candidates.

### Step 4: Pre-Refresh Keyword Research

Before refreshing, re-validate the keyword strategy:
1. Confirm the original target keyword still has volume (markets change)
2. Identify new related keywords that have emerged since original publication
3. Check if search intent has shifted (SERP has changed from blog posts to product pages, etc.)
4. Look for featured snippet, PAA, or other SERP feature opportunities
5. Find keywords this page is already ranking for (positions 10–30 in GSC) — these are "almost there" keywords to strengthen

### Step 5: Competitive Gap Analysis

1. Pull the current top 5 SERP results for the target keyword
2. Compare them to the existing content:
   - What topics/sections do they cover that the current page doesn't?
   - What's their word count vs. the current page?
   - What content formats do they use (video, comparison table, FAQ)?
   - What's their E-E-A-T signal quality (author credentials, sources cited)?
3. Create a "gap list" — specific additions the refresh must address to be competitive
4. Note any new SERP features (image pack, video carousel, featured snippet) that indicate Google's preferred format for this query

### Step 6: Technical Pre-Refresh Checks

Before editing content, verify:
1. Is the page indexed? (Check in GSC — "URL is on Google")
2. Are there any crawl errors on this URL? (GSC Coverage report)
3. Is the page's canonical URL set correctly (self-referencing)?
4. Does the URL have a redirect? (Screaming Frog — check status code)
5. Are the current internal links pointing to this page still live? (Ahrefs → Inbound links)

Fix technical issues BEFORE refreshing content.

### Step 7: Execute the Content Refresh

Refresh actions by priority:

**Level 1: Quick Win (1–2 hours)**
- Update title tag and meta description for better CTR
- Add current year to title where appropriate (only if page is about changing topic)
- Fix broken external links
- Add internal links to/from newer related content
- Update outdated statistics, tools, or product references

**Level 2: Moderate Refresh (2–4 hours)**
- Add 500–1,000 words of new content in identified gap areas
- Add new H2/H3 sections addressing PAA questions
- Add or improve FAQ section with schema
- Improve structure (add table of contents, better H2 flow)
- Update all statistics with current sources
- Add a relevant image or visual asset with optimized alt text

**Level 3: Full Rewrite (4–8+ hours)**
- Rewrite intro to hook readers faster and address current intent
- Restructure entire outline to match current SERP format expectations
- Expand total word count to match or exceed top competitor
- Add original data, case study, or unique framework section
- Full on-page SEO re-optimization with current semantic keyword set
- Add schema markup if not present
- Add downloadable asset or interactive element

### Step 8: Update the "Last Updated" Date

1. Change the published/modified date in the CMS to today
2. Add a visible "Last Updated: [Month Year]" note near the top of the article
3. Update the `dateModified` field in Article schema
4. Add an "Editor's Note" or "Update Note" box explaining what was changed (builds trust)

### Step 9: Post-Refresh Internal Link Audit

1. Identify any new related content published since the original post — add links to/from those
2. Check if any cluster articles should now link to this refreshed piece
3. Ensure the refreshed page links to the pillar page if it's part of a cluster
4. Verify all internal links from this page are still live (no 404s)

### Step 10: Submit and Monitor

1. Submit the refreshed URL in Google Search Console ("Request indexing")
2. Note the refresh date in your tracking spreadsheet
3. Track position changes weekly for 4–6 weeks after refresh
4. Expected timeline: Google typically re-evaluates and adjusts rankings within 2–6 weeks
5. If no improvement after 60 days: deepen the refresh (try Level 3 if you did Level 1/2)

### Step 11: CRO Pass (For High-Traffic Refresh Targets)

If the page also needs conversion improvement:
1. Add a relevant CTA in the first fold and last section
2. Add lead magnet or content upgrade offer (download related to the topic)
3. Check scroll depth in Hotjar — are readers dropping before the CTA?
4. Add social proof (relevant testimonials or results) near CTA
5. Test headline variations using Google Optimize

---

## Content Refresh Decision Framework

```
Is the page getting ANY impressions in the last 90 days?
├── NO → Check: any backlinks?
│   ├── YES (has backlinks) → Redirect to stronger page that covers the topic
│   └── NO (no backlinks) → Delete + redirect to category or homepage
│
└── YES → What's the avg. position?
    ├── Position 1–5 → Healthy. Add internal links, promote. Minor refresh if CTR low.
    ├── Position 6–20 → REFRESH. Add depth, fix gaps, improve E-E-A-T.
    ├── Position 21–50 → FULL REFRESH. Intent match? Word count? Semantic gaps?
    └── Position 51+ → Was this page ever ranking? Check history.
        ├── Previously ranked → Investigate cause. Penalty? Thin content? Rewrite.
        └── Never ranked → New topic targeting? May need full rethink.
```

---

## Content Refresh Brief Template

```
## CONTENT REFRESH BRIEF

**Client:** [Name]
**URL:** [existing URL — do NOT change URL unless redirecting]
**Original Publish Date:** [Date]
**Last Refreshed:** [Date or Never]
**Refresh Date:** [Today]

---

### CURRENT PERFORMANCE (pull from GSC + GA4)
- Impressions (90 days): [X]
- Clicks (90 days): [X]
- Avg Position: [X]
- CTR: [X]%
- Organic Sessions (GA4, 90 days): [X]
- Bounce Rate: [X]%

### CURRENT PRIMARY KEYWORD
[keyword] | Volume: [X] | KD: [X]

### NEW / ADDITIONAL KEYWORDS TO TARGET
- [keyword 2] — discovered in GSC position 11–30
- [keyword 3] — discovered via content gap

### REFRESH LEVEL
[ ] Level 1: Quick Win  [ ] Level 2: Moderate  [ ] Level 3: Full Rewrite

### REASON FOR REFRESH
[ ] Declining rankings  [ ] Low CTR  [ ] Outdated content  [ ] Keyword expansion  
[ ] Algorithm recovery  [ ] Thin content  [ ] Competitive gap

### CURRENT WORD COUNT
[X words]

### TARGET WORD COUNT AFTER REFRESH
[X words — based on competitor average]

### SPECIFIC GAPS TO ADDRESS
1. [Section/topic missing vs. competitors]
2. [Outdated statistic or section]
3. [No FAQ / schema present]
4. [Weak intro / high bounce from intro]

### CURRENT TITLE TAG
[current]

### NEW TITLE TAG (if changing)
[proposed — ≤60 chars]

### CURRENT META DESCRIPTION
[current]

### NEW META DESCRIPTION (if changing)
[proposed — ≤160 chars]

### NEW SECTIONS TO ADD
- H2: [New section]
- H2: [New section]
- FAQ: [New questions from PAA]

### SCHEMA TO ADD / UPDATE
[ ] Article (update dateModified)  [ ] FAQPage  [ ] HowTo  [ ] BreadcrumbList

### INTERNAL LINKS TO ADD (in this refresh)
- Link to: [URL] | Anchor: "[text]" | Location: [section to add near]
- Link from: [other URL] → this page

### BROKEN LINKS TO FIX
- [URL] needs to be replaced with [new URL]

### POST-REFRESH SUBMISSION
[ ] Submit to GSC for re-indexing
[ ] Update "Last Modified" date in CMS
[ ] Update dateModified in schema
[ ] Add "Last Updated" note in article
```

---

## Merge Strategy (When to Consolidate)

If two pages cover very similar topics and both underperform:
1. Identify which URL has more backlinks (Ahrefs) — this becomes the "keep" URL
2. Combine the best content from both pages into one comprehensive piece on the "keep" URL
3. 301 redirect the "lose" URL to the "keep" URL
4. Update all internal links pointing to the "lose" URL
5. Resubmit the consolidated page for indexing

---

## Tools & Workflow

| Tool | Purpose |
|---|---|
| Google Search Console | Performance data, coverage, indexing |
| Google Analytics 4 | Sessions, engagement, bounce rate |
| Ahrefs / Semrush | Backlink data, keyword gaps |
| Screaming Frog | Full site crawl, URL audit |
| Surfer SEO / Clearscope | Semantic optimization post-refresh |
| Hotjar / Microsoft Clarity | Scroll maps, session recordings |
| Notion / Airtable | Content audit tracking spreadsheet |

---

## Performance Metrics & KPIs

| Metric | Target After Refresh | Check At |
|---|---|---|
| Avg position improvement | +5 positions within 60 days | 30, 60 days |
| CTR improvement | +0.5–2% for title/meta refreshes | 30 days |
| Organic sessions | +20–50% within 90 days | 90 days |
| Impressions | Growing (more keyword coverage) | Monthly |
| Bounce rate | -5–15% improvement | Monthly |
| Backlinks retained | No loss from refresh | 30 days |

---

## Common Mistakes to Avoid

- Changing the URL when refreshing (kills backlink equity and triggers redirect chain)
- Removing content that was ranking for secondary keywords (check GSC for all ranking terms first)
- Refreshing without submitting to GSC for re-indexing
- Not updating the `dateModified` in schema (Google won't know content changed)
- Refreshing based on gut feeling instead of data (always audit first)
- Over-refreshing high-performing pages (if it ain't broke, add links and move on)
- Deleting pages without redirecting (creates 404s and loses backlink equity)
