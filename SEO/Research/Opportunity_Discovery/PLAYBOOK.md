# Opportunity Discovery — Playbook

## When to Use This

Use this playbook after keyword research and gap analysis are complete, when you need to identify non-obvious organic growth opportunities, when a client's "obvious" keywords are too competitive to enter quickly, when a client is in a niche with low search volume and you need to find volume from adjacent topics, or when you're building a 12-month growth roadmap. This is the synthesis layer — it transforms raw research data into a ranked, actionable opportunity stack.

---

## Step-by-Step Process

### Step 1: Aggregate All Research Inputs
Before identifying opportunities, consolidate all prior research outputs:

- [ ] Pull: Keyword Research Tier 1 list (with opportunity scores)
- [ ] Pull: SERP Analysis report (featuring snippet opportunities, weak competitor pages)
- [ ] Pull: Search Intent alignment report (intent mismatch pages)
- [ ] Pull: Competitor Research attack map
- [ ] Pull: Keyword Gap quick wins list and prioritized cluster list
- [ ] Compile all into a single "Opportunity Pool" master sheet with a source tag column (`keyword_research`, `gap_analysis`, `serp_analysis`, `competitor_research`)
- [ ] This pool should contain every identified opportunity across all research streams — deduplicate on keyword

### Step 2: Apply the Opportunity Scoring Matrix
Score every item in the opportunity pool on 5 dimensions (1–5 each, max 25):

| Dimension | 1 (Low) | 3 (Medium) | 5 (High) |
|---|---|---|---|
| **Search Volume Potential** | < 100/mo | 100–1,000/mo | > 1,000/mo |
| **Ranking Achievability** | KD 60+, DR gap > 30 | KD 30–60, DR gap 10–30 | KD < 30, DR gap < 10 |
| **Business Value** | Awareness only, no conversion path | MOFU, indirect conversion | Direct conversion (BOFU) |
| **Speed to Results** | 6+ months | 3–6 months | < 3 months |
| **Resource Cost** | New 3000+ word content + links needed | New 1000–2000 word content | Optimization of existing page |

- [ ] Calculate composite opportunity score (sum of 5 dimensions) for every item
- [ ] Sort descending → top 25% become Tier 1 opportunities
- [ ] This scoring replaces gut instinct with a repeatable, defensible prioritization model

### Step 3: Quick Win Identification (30–90 Day Window)
Quick wins are the foundation of early client trust. Identify them systematically:

**Category A: Near-Ranking Quick Wins**
- [ ] GSC: Pull all queries where client ranks 11–20 with > 100 impressions/month
- [ ] Ahrefs: Filter client's organic keywords by position 11–20, volume > 50
- [ ] For each: check if the issue is (a) weak on-page optimization, (b) missing internal links, or (c) thin content
- [ ] Quick win actions: title tag update, add internal links from high-authority pages, expand thin content by 500 words

**Category B: Featured Snippet Grabs**
- [ ] From SERP Analysis report: all featured snippets owned by competitors with DR within 20 of client
- [ ] Action: restructure existing content to match snippet format (paragraph/list/table as required)

**Category C: Thin Competitor Content**
- [ ] From Competitor Research: any top-10 result with < 800 words on a keyword with > 200/mo volume
- [ ] Action: create a better, more comprehensive version

**Category D: Technical Fix Wins**
- [ ] From Technical audit (if available): pages with indexing issues, canonical problems, or crawl blocks
- [ ] These aren't keyword opportunities per se, but fixing them can restore lost traffic fast

### Step 4: Medium-Term Opportunity Identification (3–6 Month Window)
- [ ] Identify all Full Gap clusters from Keyword Gap analysis where KD 30–55 and volume > 200/mo
- [ ] Identify all Investigation-intent clusters where no top-10 competitor has strong E-E-A-T signals (author credentials, data citations)
- [ ] Identify topic clusters where the client's existing domain expertise gives them a genuine content advantage (proprietary data, case studies, certifications)
- [ ] Flag emerging topic opportunities: keywords where search volume has grown > 30% YoY (Ahrefs volume history, Google Trends)
- [ ] Include MOFU content gaps: comparison pages, "best X" listicles, buyer guides — these are high-intent and typically under-served

### Step 5: Long-Term Authority Building Opportunities (6–12 Month Window)
- [ ] Identify 2–3 core topic clusters where the client could build genuine "topical authority" — comprehensive coverage that makes them the go-to resource
- [ ] Use Ahrefs "Topic" feature or manual cluster mapping: a topical authority cluster needs a pillar page + 5–10 supporting spoke pages + internal linking
- [ ] Identify link-worthy content concepts: original research, surveys, tools/calculators, comprehensive data visualizations, definitive guides — these attract editorial links over time
- [ ] Map the full topical authority build-out: pillar page → spoke pages → sub-spokes → estimated timeline and resource cost

### Step 6: Emerging Search Trend Discovery
Don't just chase current demand — identify emerging keywords before they peak:

- [ ] **Google Trends:** Search each seed topic → filter "Rising" queries → export breakout keywords (100%+ growth) → these are pre-peak opportunities
- [ ] **Ahrefs Volume History:** For keywords with low current volume but upward trend → note and monitor; build content early
- [ ] **Reddit / Forums:** Use Google: `site:reddit.com "how do I" [niche topic]` → questions with many upvotes = emerging search demand not yet captured by keyword tools
- [ ] **Twitter/X:** Search niche hashtags + "how to" / "question" — social questions often become Google searches 3–6 months later
- [ ] **AnswerThePublic / AlsoAsked:** Enter core topics → surface questions people are asking → identify ones with low current keyword tool volume but real human demand
- [ ] **Exploding Topics:** Tool for tracking pre-peak trend identification — check if any client-relevant topics are in growth phase

### Step 7: Local SEO Opportunity Discovery (For Local/Multi-Location Clients)
- [ ] Identify all service + location keyword combinations not currently ranking: `[service] + [city/neighborhood]`
- [ ] Check: does the client have a Google Business Profile? Optimized? (GBP optimization = fastest local traffic win)
- [ ] Run "near me" keyword research: `[service] near me` often has significant local volume
- [ ] Map: which service areas does the client serve but has no dedicated landing page for?
- [ ] Check competitor GBP profiles: how many reviews do they have? How often do they post? What categories? (Use BrightLocal or manual audit)
- [ ] Identify: local citation gaps (directories where competitors are listed but client isn't) — use Moz Local or Whitespark

### Step 8: Content Refresh Opportunity Identification
Existing content that used to rank is often a faster opportunity than creating new content:

- [ ] GSC: Date comparison — compare 0–6 months to 6–12 months → flag all pages with declining impressions (> 20% drop)
- [ ] Ahrefs: Site Explorer → Organic Pages → sort by "Traffic Change" (30 days) → find declining pages
- [ ] For each declining page: identify when the decline started (algorithm update? competitor added better content? content now outdated?)
- [ ] Classify refresh type:
  - **Data refresh:** Update statistics, dates, prices — fast win
  - **Depth refresh:** Expand content coverage — medium effort
  - **Full rewrite:** Content is structurally misaligned with current SERP — high effort but high return
- [ ] Content refresh opportunities often deliver results faster than new content because the URL already has some authority

### Step 9: Semantic Opportunity Expansion
Identify closely related topics the client should own but currently doesn't touch:

- [ ] Ahrefs: Keyword Explorer → enter any target keyword → "Also rank for" tab → shows what other keywords pages ranking for this term also rank for
- [ ] Semrush: Topic Research → expand each cluster → find adjacent questions and semantic terms
- [ ] Google Knowledge Graph: Search client's primary service → see what "Related entities" Google associates with it → these are semantic topics to cover
- [ ] Build a **Semantic Coverage Map**: core topic → primary related topics → secondary related topics → ensures no significant semantic gaps in content coverage

### Step 10: Opportunity Stack Final Ranking & Roadmap
Synthesize everything into a prioritized opportunity stack:

- [ ] Organize all opportunities by time horizon: 30-day / 90-day / 6-month / 12-month
- [ ] Within each horizon, rank by Opportunity Score (Step 2)
- [ ] Map each opportunity to a resource type: content creation, content refresh, on-page optimization, link building, technical fix, local SEO
- [ ] Estimate resource cost for each (hours of work) and expected traffic impact
- [ ] Calculate ROI estimate:
  ```
  Expected Monthly Traffic Gain = (Target keyword volume × CTR at target position) × ranking probability
  Revenue Impact = Expected Traffic × Client conversion rate × Average deal value
  ROI = Revenue Impact / Cost of Opportunity (time × hourly rate)
  ```
- [ ] Build the **12-Month Opportunity Roadmap** document (see Documentation)
- [ ] Present top 10 opportunities to client as the foundation of the SEO strategy

---

## Frameworks & Models

### Opportunity Scoring Matrix (5D Model)
Volume × Achievability × Business Value × Speed × Resource Cost — scored 1–5 on each dimension. Provides a single comparable score across all opportunity types.

### Quick Win Framework (ABCD Model)
- A: Near-ranking keywords (11–20)
- B: Featured snippet grabs
- C: Thin competitor content to beat
- D: Technical fix releases

All four categories should be represented in a 30-day quick win plan.

### Traffic Value Estimation
```
Expected Monthly Traffic = keyword_volume × CTR_at_target_position
Traffic Value = Expected Monthly Traffic × CPC (Ahrefs/Semrush)
```
Traffic value in $ terms helps communicate ROI to clients in business language.

### Topical Authority ROI Model
Calculate: if client achieves top-5 rankings for all keywords in a topical cluster, what is the total traffic + revenue potential?
```
Cluster Traffic Potential = Σ(keyword_volume × CTR_position_5) for all cluster keywords
Cluster Revenue = Cluster Traffic × client_conversion_rate × avg_deal_value
```
Use this to justify investment in a full cluster build-out vs. one-off keyword targeting.

### Opportunity Classification Grid
```
                High Business Value
                        │
  High Effort ──────────┼────────── Low Effort
                        │
                Low Business Value
```
- Top-right (High Value, Low Effort) → Do immediately (Quick Wins)
- Top-left (High Value, High Effort) → Plan carefully, sequence strategically
- Bottom-right (Low Value, Low Effort) → Do if bandwidth allows
- Bottom-left (Low Value, High Effort) → Skip entirely

---

## Tools & Specific Instructions

### Google Trends
- Enter core keywords → view 12-month and 5-year trends
- "Related queries" → "Rising" tab → breakout queries (100%+) = pre-peak opportunities
- Compare topics side by side to understand relative demand
- Download CSV for integration into opportunity master sheet

### AnswerThePublic / AlsoAsked
- Visual question maps organized by "what," "why," "how," "which," "can," "are" — each node = a content opportunity
- Export JSON or CSV → filter by relevance → add to opportunity pool
- Especially useful for finding Awareness-stage content opportunities with actual demand

### Ahrefs Keywords Explorer
- "Also rank for" tab: semantic expansion for any target keyword
- "Volume History": trend direction for any keyword
- "Questions" filter: sub-intent mining
- "Newly discovered" filter in Site Explorer: find keywords competitors started ranking for in the last 30 days (early competitor signals)

### Google Search Console
- Performance → Queries → sort by "Impressions" descending → look for queries with high impressions but low clicks (CTR < 2%) — these are near-ranking pages that need optimization
- Date comparison → find all declining queries → flag for content refresh

### BrightLocal (Local SEO)
- Citation Tracker: finds where client is listed and isn't vs. competitors
- Local Search Grid: visualize local pack rankings by geography
- GBP Audit: analyze Google Business Profile completeness

### Exploding Topics
- Free/paid tool tracking pre-peak keyword trends
- Filter by niche → export growing topics → identify which are relevant to client's business
- Particularly valuable for clients in fast-moving industries (tech, health, finance)

### Clearscope / Surfer SEO (Content Optimization)
- For each opportunity keyword: run through Clearscope or Surfer → get a content optimization score target and required semantic terms
- Use as the content brief foundation: ensures new content covers all required semantic entities
- Pass to content team with target score (e.g., "achieve Clearscope score > 75")

---

## Documentation & Storage

### File Structure
```
/SEO/Research/Opportunity_Discovery/
  PLAYBOOK.md
  [client-slug]/
    raw/
      google_trends_exports/
      answer_the_public_exports/
      emerging_trends_YYYY-MM-DD.csv
    processed/
      opportunity_pool_master_YYYY-MM-DD.csv
      quick_wins_YYYY-MM-DD.csv
      opportunity_scores_YYYY-MM-DD.csv
    reports/
      Opportunity_Discovery_Report_[client]_YYYY-MM-DD.md
      12_Month_Opportunity_Roadmap_[client]_YYYY-MM-DD.md
```

### Opportunity Pool Master Sheet Columns
```
opportunity_id | keyword | cluster | source | volume | KD | CPC | intent | funnel_stage | gap_type | current_rank | volume_score | achievability_score | business_value_score | speed_score | resource_score | total_opportunity_score | time_horizon | action_type | estimated_hours | expected_monthly_traffic | estimated_traffic_value | notes
```

### 12-Month Opportunity Roadmap Template
```markdown
# 12-Month SEO Opportunity Roadmap — [Client Name]
**Created:** YYYY-MM-DD
**Engagement Start:** YYYY-MM-DD

## Executive Summary
- Total opportunities identified: X
- Expected traffic at month 12: X visits/mo
- Expected traffic value at month 12: $X/mo
- Investment required: X hours / month

## Quick Wins (Month 1–2)
| # | Opportunity | Type | Expected Traffic | Effort | Owner |
|---|---|---|---|---|---|

## Foundation Build (Month 2–4)
| # | Opportunity | Type | Expected Traffic | Effort | Owner |
|---|---|---|---|---|---|

## Authority Clusters (Month 4–8)
| # | Cluster | Page Count | Expected Traffic | Effort | Owner |
|---|---|---|---|---|---|

## Long-Tail Expansion (Month 8–12)
| # | Opportunity | Type | Expected Traffic | Effort | Owner |
|---|---|---|---|---|---|

## Monthly Traffic Projection
| Month | Cumulative Traffic | Traffic Value | Milestone |
|---|---|---|---|
| 1 | | | |
| 3 | | | |
| 6 | | | |
| 9 | | | |
| 12 | | | |

## Resource Requirements Summary
- Content creation: X pages × X hours avg = X total hours
- Content refresh: X pages × X hours avg = X total hours
- On-page optimization: X pages × X hours avg = X total hours
- Link building: X hours/month
- Technical: X hours (one-time)
```

---

## Prioritization Framework

The opportunity stack is organized in this definitive priority order:

1. **Technical fixes that unlock suppressed rankings** — if pages are being blocked, canonicalized wrong, or have index issues, fix these FIRST before any content work; they deliver immediate results
2. **Near-ranking quick wins (Rank 11–20)** — pages already getting impressions and close to page 1; on-page optimization can move them in 30–60 days
3. **Featured snippet captures** — structured content updates; low effort, visible impact, fast results
4. **BOFU content gaps** — new transactional landing pages or service pages; direct revenue impact even with modest traffic
5. **MOFU investigation content** — comparison pages, buyer guides, "best of" content; captures high-intent users close to converting
6. **High-volume cluster authority builds** — biggest traffic potential but 4–8 month timeline; start early in the engagement
7. **Emerging trend content** — plant the flag before keywords peak; high upside but longer time to return
8. **TOFU awareness content** — important for long-term brand authority but lowest immediate revenue impact; tackle after foundation is built

**Guiding principle:** Every opportunity must pass the "Business Value Test" — if a keyword won't contribute to client revenue (directly or through brand awareness that feeds a clear funnel), it doesn't belong in the roadmap, regardless of how high its volume is.
