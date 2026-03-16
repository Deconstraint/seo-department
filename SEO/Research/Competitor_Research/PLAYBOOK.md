# Competitor Research — Playbook

## When to Use This

Run competitor research at the start of every new client engagement, when launching into a new keyword vertical, when a client's rankings drop and you need to understand what changed in the competitive landscape, when building a link acquisition strategy, or when identifying content gaps. This playbook answers the question: "Who are we fighting, and how do we beat them?"

---

## Step-by-Step Process

### Step 1: Identify True Organic Competitors
Critical distinction: organic competitors are not the same as business competitors. A company can be a direct business rival but irrelevant in organic search (and vice versa).

- [ ] In Ahrefs: Site Explorer → client domain → "Competing Domains" → export top 20 domains by keyword overlap
- [ ] In Semrush: Domain Overview → client domain → "Organic Competitors" → export top 20
- [ ] Cross-reference both lists: any domain appearing in both is a high-confidence organic competitor
- [ ] Add any business competitors the client names — even if they don't appear in the overlap lists, the client considers them threats
- [ ] Remove irrelevant domains: news sites, Wikipedia, YouTube (unless client is in media/video) — focus on same-format sites
- [ ] Final list: 5–8 true organic competitors for deep analysis

### Step 2: Competitor Domain Authority & Trust Profile
For each competitor:

- [ ] Record: Domain Rating (Ahrefs), Domain Authority (Moz), Trust Flow (Majestic), total referring domains, total backlinks
- [ ] Note: how long has the domain existed? (Whois lookup or Ahrefs "Domain History")
- [ ] Check: organic traffic estimate (Ahrefs Site Explorer → Organic Traffic)
- [ ] Check: total number of pages indexed (site: operator in Google, or GSC if client, or Ahrefs "Best by Links" filter)
- [ ] Build the **Competitor Authority Benchmark**: where does the client's DR sit relative to the top 3 organic competitors? This gap directly informs link building targets.

### Step 3: Organic Keyword Footprint Analysis
For each competitor:

- [ ] Ahrefs: Site Explorer → Organic Keywords → set filter: position 1–10 → export (max 1,000 rows)
- [ ] Ahrefs: Site Explorer → Organic Keywords → set filter: position 1–3 → export (these are their strongest pages)
- [ ] Record: total organic keywords ranking in top 10, total estimated organic traffic value (Ahrefs Traffic Value metric)
- [ ] Identify: which keyword clusters does each competitor dominate? (group by Ahrefs Parent Topic)
- [ ] Flag: which of their top-traffic pages address topics the client doesn't currently have content for?

### Step 4: Content Strategy Reverse-Engineering
Identify what content types and formats drive the most traffic for each competitor:

- [ ] Ahrefs: Site Explorer → Top Pages (sort by Traffic) → examine top 20 pages for each competitor
- [ ] Categorize each top page: blog post, service page, tool/calculator, comparison page, case study, landing page
- [ ] Note content formats that appear repeatedly in the top 20 — this reveals their successful content strategy
- [ ] Record: average word count of their top 10 pages (use SEOquake or Screaming Frog)
- [ ] Check: do they use a content hub/pillar model? Look for internal linking patterns to an authoritative pillar page
- [ ] Document: their content publishing frequency (Ahrefs → "New pages" filter — how many pages did they add last month?)

### Step 5: Backlink Profile Deep-Dive
- [ ] Ahrefs: Site Explorer → Referring Domains → filter: DR 30+ → export
- [ ] Categorize referring domains: news/media, industry blogs, directories, government/education, forums, partnerships
- [ ] Identify "link patterns": are their links primarily from guest posts? PR mentions? Resource pages? Broken link replacements? HARO?
- [ ] Find "link targets": which of their backlink sources link to multiple competitors? (These are link-friendly sites that accept links in this niche)
- [ ] Ahrefs: "Link Intersect" tool → enter all competitors → see domains linking to all of them but NOT the client → these are your highest-priority outreach targets
- [ ] Record: the top 20 link acquisition opportunities with domain metrics (DR, monthly traffic, relevance)

### Step 6: Anchor Text Profile Analysis
- [ ] Ahrefs: Anchors report for each competitor → note the ratio of: exact match, partial match, branded, naked URL, generic ("click here")
- [ ] Flag over-optimized anchor profiles: if a competitor has > 30% exact-match anchors, they are at risk of a Penguin-style penalty — don't copy their profile
- [ ] Use as a benchmark: what does a natural anchor profile look like for sites ranking in this niche?
- [ ] Build a recommended anchor text distribution for client's link building campaign

### Step 7: Technical Competitiveness Assessment
For each competitor's top 5 traffic pages:

- [ ] Run through Google PageSpeed Insights → record Core Web Vitals (LCP, FID/INP, CLS) scores
- [ ] Check mobile-friendliness: Google's Mobile-Friendly Test
- [ ] Note page structure: do they use schema markup? (Check with Schema Markup Validator or RichResults Test)
- [ ] Check if they have AMP pages (relevant for news/informational content)
- [ ] Use Wappalyzer to identify their tech stack — note if they use a CMS, CDN, or specific SEO plugins

### Step 8: SERP Visibility Share Analysis
- [ ] Semrush: Domain Overview → compare client + all 5–8 competitors side by side → export visibility trend over 12 months
- [ ] Ahrefs: "Share of Voice" — not native, but calculate: (client organic traffic / sum of all competitor traffic) × 100 = client's share
- [ ] Identify: is any competitor rapidly growing or declining in visibility? Growing competitors = study their recent content and links; declining = potentially plagued by a penalty or poor content quality
- [ ] Track Share of Voice monthly for top competitor set — this is the key competitive KPI

### Step 9: Paid Search Intelligence (Signal Mining)
Even if the client isn't running PPC, competitor paid search reveals their highest-value keywords:

- [ ] Semrush: Advertising Research → enter each competitor → export their paid keywords and ad copy
- [ ] Logic: companies don't bid on keywords that don't convert — their top paid keywords are their confirmed high-intent, high-value terms
- [ ] Add competitor paid keywords to the master keyword list with tag `competitor_paid` — prioritize these for organic capture
- [ ] Study ad copy: what value propositions, pain points, and CTAs do they emphasize? Use this for content framing and meta description writing

### Step 10: Featured Snippet & SERP Feature Ownership
- [ ] Semrush: Position Tracking → enter all competitor domains → filter by "SERP Features" → see which features they own
- [ ] Ahrefs: Keyword Explorer → search any target keyword → SERP Overview → look for Featured Snippet ownership
- [ ] Record for each competitor: how many featured snippets do they own? How many PAA boxes? Local pack appearances?
- [ ] If a competitor owns multiple featured snippets → study their structured FAQ and How-To markup
- [ ] Target featured snippets owned by lower-authority competitors first (DR within 15 of client's DR)

### Step 11: Competitive Gap Summary & Attack Map
- [ ] Compile all findings into the **Competitor Research Report** (see Documentation)
- [ ] Build the **Attack Map**: for each competitor weakness identified, what is the offensive action?
  - Thin content → produce a definitively better piece
  - Few backlinks on a ranking page → outrank with link building
  - No local signals → beat with local SEO
  - Slow site → technical advantage if client site is fast
  - Old content (2+ years no update) → publish fresher, deeper version

---

## Frameworks & Models

### Competitive Authority Matrix
Rate each competitor on 5 dimensions (0–10 each):

| Dimension | Description |
|---|---|
| Domain Authority | DR/DA score normalized to 0–10 |
| Content Volume | Total indexed pages (log scale) |
| Content Quality | Depth + freshness + E-E-A-T signals |
| Backlink Power | Referring domains + quality distribution |
| Technical Quality | Core Web Vitals + mobile + schema |

Total max = 50. Client score vs. competitor scores reveals where to invest.

### Link Intersect Model
Sites linking to all competitors but not client = highest-priority link opportunities. These sites have demonstrated willingness to link in this niche.

### Share of Voice (SOV) Formula
```
Client SOV = (Client Organic Traffic) / (Client + All Competitor Traffic) × 100
```
Track monthly. Target: grow SOV by 5–10% per quarter in primary keyword clusters.

### Competitor Vulnerability Index
Score each competitor's top 10 pages on:
- Content age (older = more vulnerable): 1–5
- Word count vs. top SERP (less = more vulnerable): 1–5
- Backlinks to page (fewer = more vulnerable): 1–5
- DR of domain (lower = more vulnerable): 1–5

Total score 4–8 = vulnerable; 16–20 = strongly defended. Target vulnerable pages first.

---

## Tools & Specific Instructions

### Ahrefs
- **Competing Domains:** Site Explorer → domain → "Competing Domains" tab — instant competitor identification
- **Content Gap:** Site Explorer → client domain → "Content Gap" → enter up to 10 competitor domains → export missing + weak keywords
- **Link Intersect:** Site Explorer → "Link Intersect" tab → enter up to 10 domains → find unshared backlink sources
- **Top Pages:** Site Explorer → competitor → "Top Pages" sorted by traffic → study their best content

### Semrush
- **Domain vs. Domain:** Domain Overview → "Compare to" → add up to 4 competitors → side-by-side metrics
- **Traffic Analytics:** See estimated traffic, pages per visit, bounce rate for competitor domains
- **Advertising Research:** Competitor paid keywords — mine for high-intent organic targets
- **Sensor:** Check niche-level SERP volatility score for context during competitive analysis

### Majestic
- Trust Flow / Citation Flow metrics provide a different perspective on link quality than Ahrefs DR
- Use for verifying quality of specific backlink opportunities: TF > 20 is a reasonable benchmark for a quality link

### SimilarWeb
- Traffic source breakdown: what % of competitor traffic is organic vs. paid vs. social vs. direct?
- Geographic distribution: where is their audience? (Critical for local SEO clients)
- Top referral sources: which sites drive referral traffic to competitors? (Potential partnerships/links)

### SpyFu
- Long-term keyword history: shows what keywords competitors have ranked for over years (not just current snapshot)
- Useful for identifying keywords they've abandoned (potential opportunity) or recently entered (new competition signal)

---

## Documentation & Storage

### File Structure
```
/SEO/Research/Competitor_Research/
  PLAYBOOK.md
  [client-slug]/
    raw/
      competitor_keywords_[domain]_YYYY-MM-DD.csv
      competitor_backlinks_[domain]_YYYY-MM-DD.csv
      link_intersect_YYYY-MM-DD.csv
    processed/
      competitive_analysis_master_YYYY-MM-DD.csv
      attack_map_YYYY-MM-DD.md
    reports/
      Competitor_Research_Report_[client]_YYYY-MM-DD.md
```

### Competitor Research Report Template
```markdown
# Competitor Research Report — [Client Name]
**Date:** YYYY-MM-DD
**Competitors Analyzed:** [domain1, domain2, ...]

## Competitive Landscape Summary
| Metric | Client | Competitor 1 | Competitor 2 | Competitor 3 |
|---|---|---|---|---|
| Domain Rating | | | | |
| Referring Domains | | | | |
| Organic Keywords (1-10) | | | | |
| Est. Monthly Traffic | | | | |
| Share of Voice | | | | |

## Competitor Content Strategy
[Summary of formats, topics, publishing frequency for each competitor]

## Top Link Acquisition Opportunities
| Domain | DR | Relevance | Current Links To | Opportunity Type |
|---|---|---|---|---|

## Attack Map
| Competitor | Weakness | Client Advantage | Action | Priority |
|---|---|---|---|---|

## Featured Snippet Targets
| Keyword | Current Owner | DR | Action |
|---|---|---|---|

## Recommended Competitive Focus Areas
1. [Top recommendation]
2. [Second recommendation]
3. [Third recommendation]
```

---

## Prioritization Framework

1. **Link Intersect targets** — sites already linking to competitors will link to you; highest-probability outreach
2. **Vulnerable competitor pages** — low vulnerability index score on high-volume keywords → create better content, earn their rankings
3. **Paid keyword mining** — competitor PPC keywords confirm high-intent organic targets; these are pre-validated revenue drivers
4. **Share of Voice gaps** — identify clusters where top competitors are weak or declining; enter those clusters aggressively
5. **Featured snippet capture** — from competitors with lower DR than client; fastest visibility gains with a focused content update

Never try to directly compete with a dominant competitor across all their keywords simultaneously. Pick 2–3 clusters where they are weakest and build concentrated topical authority there first.
