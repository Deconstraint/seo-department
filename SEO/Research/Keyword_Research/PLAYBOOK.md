# Keyword Research — Playbook

## When to Use This

Load this playbook at the start of any new client engagement, during a site audit, when launching a new product/service page, when entering a new market, or when organic traffic has plateaued and a fresh keyword strategy is needed. This is the foundation of all SEO work — do not skip it.

---

## Step-by-Step Process

### Step 1: Client & Business Discovery
- [ ] Obtain a completed client intake form covering: core services/products, target audience, geography, revenue goals, and existing content
- [ ] Identify 3–5 "seed" topics directly tied to revenue (e.g., "personal injury attorney," "SaaS project management," "commercial roofing Denver")
- [ ] Review the client's existing GSC data: export the full query report for the trailing 12 months (filter: clicks > 0)
- [ ] Note branded vs. non-branded query split — this reveals current organic authority vs. demand

### Step 2: Seed Keyword Expansion
- [ ] In **Ahrefs Keyword Explorer**: enter each seed term → run "Matching terms" + "Related terms" → export all results (no filter yet)
- [ ] In **Semrush Keyword Magic Tool**: repeat the same seed list → export "Broad Match" results for each
- [ ] In **Google Search Console**: export the full Queries report (all time) → filter by position > 20 to surface keywords the site ranks for but doesn't own yet
- [ ] In **Google Keyword Planner**: enter all seed terms → export "Keyword Ideas" with avg monthly searches and competition

### Step 3: Competitor Seed Extraction
- [ ] Identify 3–5 true organic competitors (not brand competitors — sites ranking for the same keywords)
- [ ] In Ahrefs: Site Explorer → each competitor URL → "Organic Keywords" → filter: position 1–20 → export
- [ ] In Semrush: Domain Overview → Organic Research → export keyword list for each competitor
- [ ] Merge all competitor keyword lists into a master CSV — label by source

### Step 4: Master Keyword List Assembly
- [ ] Combine all exports into a single Google Sheet (columns: keyword, volume, KD, CPC, source, competitor_found_on)
- [ ] Deduplicate on keyword string (use `=UNIQUE()` or Python pandas `drop_duplicates()`)
- [ ] Remove keywords with < 10 monthly searches unless they are high-CPC (> $5) or exact-match brand terms
- [ ] Remove pure navigational queries (brand + "login," brand + "careers," etc.)

### Step 5: Keyword Difficulty Scoring
Apply a composite KD score using the **3-Factor KD Model**:

| Factor | Weight | Source |
|---|---|---|
| Ahrefs KD score | 40% | Ahrefs Keyword Explorer |
| SERP authority (avg DR of top 10) | 35% | Ahrefs SERP Overview |
| Content depth required (estimated) | 25% | Manual SERP review |

- [ ] For each keyword: pull Ahrefs KD + average DR of top 10 results
- [ ] Estimate content depth: "thin" (< 800 words), "medium" (800–2000), "deep" (2000+) based on top-3 result word counts
- [ ] Score each keyword 1–100 using weighted formula: `(Ahrefs_KD × 0.4) + (avg_DR × 0.35) + (depth_score × 0.25)` where depth_score = thin:20, medium:50, deep:80
- [ ] Label: Easy (< 30), Medium (30–60), Hard (60+)

### Step 6: Intent Classification
Classify every keyword using the **CTBA Framework** (Commercial, Transactional, Brand, Awareness):

| Intent | Signals | Target Content Type |
|---|---|---|
| Commercial | "best," "top," "vs," "review," "compare" | Comparison page, listicle, buyer guide |
| Transactional | "buy," "hire," "get," "near me," "price," "cost" | Service page, product page, landing page |
| Brand | Client name, product name | Homepage, About, branded landing |
| Awareness | "how to," "what is," "why," "guide," "tips" | Blog post, pillar page, FAQ |

- [ ] Add an `intent` column to the master sheet and classify each keyword
- [ ] For ambiguous keywords, check the SERP — if top results are listicles, classify as Commercial; if service pages, Transactional

### Step 7: Topic Clustering
- [ ] Group keywords by semantic topic using Ahrefs "Parent Topic" column as the primary cluster signal
- [ ] Create cluster groups: one "pillar" keyword per cluster (highest volume, medium KD) + supporting "spoke" keywords (longer tail, lower KD)
- [ ] Each cluster should map to one URL on the site — do not create two pages targeting the same cluster
- [ ] Name each cluster by its pillar keyword and document cluster size (number of keywords per cluster)

### Step 8: Opportunity Scoring
Apply the **Opportunity Score Formula** to each keyword:

```
Opportunity Score = (Monthly Volume × CTR_estimate) × (1 / KD_composite) × Intent_multiplier
```

CTR estimates by position: #1 = 28%, #2 = 15%, #3 = 11%, #4–10 = 3–7%
Intent multipliers: Transactional = 1.5, Commercial = 1.3, Awareness = 1.0, Brand = 0.8

- [ ] Calculate for each keyword using current ranking position (or position 10 if not ranking)
- [ ] Sort descending — top 20% are your Tier 1 targets

### Step 9: Current Ranking Gap Analysis
- [ ] Cross-reference master keyword list against GSC data — mark keywords where: (a) client ranks 11–30 (quick win potential), (b) client has no ranking (new content needed), (c) client ranks 1–10 (defend and optimize)
- [ ] Flag "quick wins": keywords where client ranks 11–20, volume > 100/mo, and KD < 45 — these get immediate attention

### Step 10: Final Deliverable Assembly
- [ ] Create the **Keyword Research Report** (see Documentation section below)
- [ ] Export a prioritized Tier 1 target list (max 50 keywords for a new engagement)
- [ ] Map each Tier 1 keyword to an existing or new URL
- [ ] Hand off Tier 1 list to Content and On-Page teams with intent and cluster data

---

## Frameworks & Models

### Keyword Difficulty (3-Factor KD Model)
- Ahrefs KD (40%) + Avg DR of top 10 (35%) + Content depth required (25%)
- Calibrated to site's current DR — a DR 20 site should target KD < 30; DR 50+ site can target KD < 55

### Intent Classification (CTBA Framework)
- Commercial / Transactional / Brand / Awareness
- Always verify with SERP — tool classification is often wrong for local and niche terms

### Topic Clustering (Hub & Spoke)
- One pillar page per topic cluster
- Spoke pages link back to pillar, pillar links out to spokes
- Cluster size: 3–12 keywords per cluster (ideal)

### Opportunity Scoring
- Combines volume, CTR, difficulty, and intent into a single ranked score
- Re-calculate monthly as rankings shift

---

## Tools & Specific Instructions

### Ahrefs
- **Keyword Explorer:** Enter seed → Matching Terms → filter KD 0–60 → export CSV
- **Site Explorer → Organic Keywords:** Competitor domains → export top 1000 keywords
- **SERP Overview:** Check manually for any keyword before writing content — look for Featured Snippet, People Also Ask, video carousels

### Semrush
- **Keyword Magic Tool:** Seed → Broad Match → Group by topic → export
- **Keyword Gap Tool:** Client domain vs. 3 competitors → filter "Missing" and "Weak" → export (this feeds directly into Keyword Gap playbook)

### Google Search Console
- Performance → Search Results → export all queries (set date range to max available)
- Filter: impressions > 10 → sort by position descending → find 11–30 range opportunities

### Google Keyword Planner
- Tools → Keyword Planner → Discover new keywords → enter seeds → download CSV
- Use for CPC data (PPC value signal) and local volume estimates

### Python / Sheets Automation
- Deduplication: `df.drop_duplicates(subset='keyword', keep='first')`
- Opportunity score: use pandas formula column
- Pivot by cluster: `df.groupby('cluster').agg({'volume': 'sum', 'opportunity_score': 'mean'})`

---

## Documentation & Storage

### File Structure
```
/SEO/Research/Keyword_Research/
  PLAYBOOK.md                    ← this file
  [client-slug]/
    raw/
      ahrefs_export_YYYY-MM-DD.csv
      semrush_export_YYYY-MM-DD.csv
      gsc_export_YYYY-MM-DD.csv
    processed/
      master_keyword_list_YYYY-MM-DD.csv
      tier1_targets_YYYY-MM-DD.csv
    reports/
      Keyword_Research_Report_[client]_YYYY-MM-DD.md
```

### Keyword Research Report Template
```markdown
# Keyword Research Report — [Client Name]
**Date:** YYYY-MM-DD
**Prepared by:** [Agent/Analyst]

## Summary
- Total keywords analyzed: X
- Tier 1 targets identified: X
- Quick win opportunities: X
- Estimated traffic potential (Tier 1): X visits/mo at position 1

## Tier 1 Target Keywords
| Keyword | Volume | KD | Intent | Current Rank | Opportunity Score |
|---|---|---|---|---|---|

## Topic Clusters
| Cluster Name | Pillar Keyword | Spoke Count | Total Volume | Priority |
|---|---|---|---|---|

## Quick Wins (Rank 11–20)
| Keyword | Current Rank | Volume | Action Needed |
|---|---|---|---|

## Recommendations
1. [Top 3 immediate actions]
```

---

## Prioritization Framework

Prioritize in this order:

1. **Quick Wins** — Currently ranking 11–20, volume > 100, KD < 45 → On-page optimization, internal linking, content refresh
2. **High-Intent, Low-KD** — Transactional or Commercial intent, KD < 35, volume > 50 → New content or dedicated landing pages
3. **Topic Cluster Pillars** — Build topical authority before targeting individual keywords
4. **High-Volume, High-KD** — Only pursue if client has DR > 40 and content budget for 3000+ word assets

**Do not chase volume alone.** A 200/mo keyword with transactional intent and KD 25 is worth more than a 2,000/mo informational keyword with KD 70 for most clients.
