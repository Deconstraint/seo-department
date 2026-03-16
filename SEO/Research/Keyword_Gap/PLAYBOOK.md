# Keyword Gap Analysis — Playbook

## When to Use This

Run keyword gap analysis at the start of every engagement after initial competitor identification, quarterly as competitive landscapes shift, before any major content sprint, when a client's organic traffic growth has stalled, or when you want to identify fast-content opportunities where competitors are winning traffic but the client has zero presence. Keyword gap analysis turns competitor strength into your content roadmap.

---

## Step-by-Step Process

### Step 1: Set Up the Comparison Framework
- [ ] Confirm the competitor list from Competitor Research playbook (5–8 organic competitors)
- [ ] Select 3–5 of the strongest organic competitors for the gap analysis (Semrush Keyword Gap limits to 4 competitors + 1 target domain)
- [ ] Ensure you have fresh exports from the last 30 days — stale competitor data will give inaccurate gap results
- [ ] Define the scope: full-site keyword gap (all keywords) or page-level gap (specific subfolder, e.g., /blog/ or /services/)

### Step 2: Run the Semrush Keyword Gap Tool
This is the primary tool for structured gap analysis:

- [ ] Navigate to Semrush → Keyword Gap tool
- [ ] Enter client domain in the "You" field
- [ ] Enter up to 4 competitor domains in the competitor fields
- [ ] Set match type: "Organic" (also run separately for "Paid" to capture paid keyword intelligence)
- [ ] Click "Compare" → Semrush will show overlap and gap data
- [ ] Filter by: **"Missing"** (keywords all competitors rank for but client has zero ranking) → export full list
- [ ] Filter by: **"Weak"** (keywords where client ranks lower than all competitors) → export full list
- [ ] Filter by: **"Untapped"** (keywords where some but not all competitors rank, client does not) → export full list
- [ ] Do NOT neglect "Unique to you" — keywords only the client ranks for (defend these, they're your moats)

### Step 3: Run the Ahrefs Content Gap Tool
Run this in parallel for cross-validation and additional data:

- [ ] Ahrefs → Site Explorer → enter client domain → "Content Gap" tab
- [ ] Enter all competitor domains in the "Show keywords that these targets rank for" field
- [ ] Set filter: "But the following target doesn't rank for" → client domain
- [ ] Set position filter: 1–20 (only keywords where competitors have actual visibility)
- [ ] Export full results (up to 10,000 rows)
- [ ] Run a second pass with position filter 1–10 for the highest-value gaps

### Step 4: Merge & Deduplicate Gap Lists
- [ ] Combine Semrush "Missing" + "Weak" + Ahrefs Content Gap exports into one master sheet
- [ ] Add a column: `gap_type` (Missing / Weak / Untapped)
- [ ] Add a column: `competitor_count` — how many competitors rank for this keyword? (higher = more validated demand)
- [ ] Deduplicate on keyword string
- [ ] Remove branded keywords (competitor names, product names) unless client offers a comparison/alternative
- [ ] Remove keywords with volume < 20/mo (unless CPC > $10 — high-value long tail)

### Step 5: Gap Categorization by Cluster
- [ ] Group all gap keywords by topic cluster using Ahrefs "Parent Topic" or manual grouping by semantic similarity
- [ ] For each cluster: record total keyword count, total monthly volume, average KD, number of competitors owning the cluster
- [ ] Classify each cluster as:
  - **Full Gap:** Client has zero content addressing this cluster
  - **Partial Gap:** Client has related content but it's not properly optimized or targeted
  - **Ranking Gap:** Client has the right page but it's under-performing vs. competitors

### Step 6: Intent Layer — Filter for Monetizable Gaps
Not all gaps are worth filling. Apply intent filtering:

- [ ] For each gap cluster, classify primary intent (use Search Intent playbook AITO model)
- [ ] Prioritize gaps in this order: Transactional > Investigation > Awareness
- [ ] Eliminate from immediate priority: pure Orientation keywords (these belong to competitors' brands)
- [ ] Flag high-CPC gaps: CPC > $5 + intent = Transactional → these are your highest revenue-impact gaps
- [ ] Calculate "Gap Value Score" per cluster:
  ```
  Gap Value Score = Total Cluster Volume × Intent Multiplier × Competitor Count Weight
  Intent: Transaction=1.5, Investigation=1.3, Awareness=1.0
  Competitor Count Weight: 4/4 competitors rank = 1.5x; 3/4 = 1.3x; 2/4 = 1.1x; 1/4 = 0.9x
  ```

### Step 7: Keyword Difficulty Filter for Quick Wins
- [ ] Within each gap cluster, identify "quick win" keywords: KD < 35 AND volume > 50 AND intent = Transactional or Investigation
- [ ] For "Full Gap" clusters with quick win keywords: these are the first content creation priorities
- [ ] For "Partial Gap" clusters: check if an existing page can be updated/expanded vs. needing a new page (prefer update — faster and preserves any existing authority)
- [ ] Create a "Gap Quick Wins" shortlist (max 30 keywords) — these can be addressed in the first 60 days

### Step 8: Competitive Difficulty Assessment per Gap
For each gap cluster, understand WHY the client is missing:

- [ ] Check: does the client have any content attempting to rank for this cluster? (GSC + Ahrefs)
  - No content at all → **Content Gap** (create new page)
  - Content exists but ranks 50+ → **Optimization Gap** (content quality or link issue)
  - Content exists and ranks 11–30 → **Ranking Gap** (quick win through on-page improvements)
- [ ] For Content Gaps: check competitor page quality — if all competitors have thin content (< 800 words), this is an easy entry point
- [ ] For Ranking Gaps: check if the ranking issue is domain authority (need links) or content quality (need rewrite)
- [ ] Document the root cause for each cluster in the gap master sheet

### Step 9: Map Gaps to the Content Calendar
- [ ] Sort gap clusters by Gap Value Score (calculated in Step 6) → top 10 clusters = Tier 1 content priorities
- [ ] For each Tier 1 cluster, determine: new page needed, or existing page update?
- [ ] Estimate production time: new long-form page = 5–7 days; content refresh = 2–3 days
- [ ] Assign to content calendar quarters:
  - Q1 (first 90 days): All Quick Wins + Top 3 Full Gap clusters
  - Q2: Next 4–6 Full Gap clusters + Partial Gap updates
  - Q3+: Lower-priority awareness clusters + long-tail expansion

### Step 10: Track Gap Closure Over Time
Set up ongoing monitoring to measure how gaps close as content is produced:

- [ ] Export the gap master sheet as a baseline (date-stamped)
- [ ] Run the gap analysis again monthly → compare: which gap keywords has the client entered the top 20 for?
- [ ] Calculate "Gap Closure Rate": (keywords entered top 20 / total gap keywords) × 100 — monthly
- [ ] Track in the client's reporting dashboard (see Documentation section)
- [ ] Re-run full gap analysis quarterly to discover new gaps as competitors publish new content

### Step 11: Defensive Gap Monitoring
- [ ] Identify keywords the client UNIQUELY owns (Semrush "Unique to You" filter)
- [ ] Check each month: are competitors starting to target these keywords?
- [ ] For any unique keyword where a competitor newly enters the top 20: flag immediately and strengthen that content (refresh + add links)
- [ ] These are your moat keywords — protect them aggressively

---

## Frameworks & Models

### Gap Taxonomy
| Gap Type | Definition | Action |
|---|---|---|
| Full Gap | Client has zero ranking, 2+ competitors rank in top 20 | Create new content |
| Partial Gap | Client has some content but below position 20 | Optimize or expand existing |
| Ranking Gap | Client ranks 11–20, competitors rank 1–10 | On-page + links |
| Defensive Gap | Client ranks 1–10, competitors entering | Strengthen and defend |

### Gap Value Score Formula
```
Gap Value = (Volume × Intent_Multiplier) × Competitor_Weight
```
Ranks every gap cluster by potential revenue impact. Use to sequence the content calendar.

### Gap Closure Tracking Model
Monthly metric: what % of identified gap keywords has the client entered the top 20 for since engagement start?
- 0–10%: Content production needs acceleration
- 10–25%: Normal healthy growth
- 25%+: Excellent — expand gap analysis to new clusters

### Content Velocity Benchmark
How fast are competitors publishing new content?
- Use Ahrefs "New Pages" report for each competitor
- If competitors publish 20+ pages/month → content velocity matters; client needs to keep pace
- If competitors publish < 5 pages/month → quality beats quantity; focus on depth over speed

---

## Tools & Specific Instructions

### Semrush Keyword Gap
- Primary tool for structured gap analysis
- Four filter types: Missing / Weak / Untapped / Unique — use all four
- Export each filter separately for cleaner data processing
- Run paid keyword gap in addition to organic — identifies high-intent terms worth targeting organically

### Ahrefs Content Gap
- Better for large-scale data (handles 10,000+ keyword exports)
- "Parent Topic" grouping reduces noise — set this filter to collapse long-tail variants
- Run at domain level AND at folder level (/blog/, /services/) for page-type-specific gaps

### Google Search Console
- Performance → Search Results → filter "Pages" → for each client page, see what keywords it's NOT ranking for that it should be
- Compare impression count to click count: high impressions + low CTR on a keyword = client has weak ranking for that term (optimization gap, not content gap)
- Date comparison: compare last 3 months to previous 3 months → keywords with declining impressions may indicate competitor encroachment

### Python / Pandas for Gap Processing
```python
import pandas as pd

# Load exports
semrush_missing = pd.read_csv('semrush_missing.csv')
ahrefs_gap = pd.read_csv('ahrefs_content_gap.csv')

# Merge and deduplicate
combined = pd.concat([semrush_missing, ahrefs_gap])
combined = combined.drop_duplicates(subset='Keyword')

# Filter: volume > 20, KD < 60
filtered = combined[(combined['Volume'] > 20) & (combined['KD'] < 60)]

# Sort by gap value score
filtered['gap_value'] = filtered['Volume'] * filtered['intent_multiplier']
filtered = filtered.sort_values('gap_value', ascending=False)
```

### KeywordSpy / iSpionage
- Alternative tools for paid keyword intelligence
- Useful when Semrush data seems thin for a niche

---

## Documentation & Storage

### File Structure
```
/SEO/Research/Keyword_Gap/
  PLAYBOOK.md
  [client-slug]/
    raw/
      semrush_missing_YYYY-MM-DD.csv
      semrush_weak_YYYY-MM-DD.csv
      semrush_untapped_YYYY-MM-DD.csv
      ahrefs_content_gap_YYYY-MM-DD.csv
    processed/
      gap_master_list_YYYY-MM-DD.csv
      gap_clusters_YYYY-MM-DD.csv
      quick_wins_YYYY-MM-DD.csv
    reports/
      Keyword_Gap_Report_[client]_YYYY-MM-DD.md
    tracking/
      gap_closure_tracker_YYYY-MM-DD.csv
```

### Gap Master List Columns
```
keyword | volume | KD | CPC | intent | gap_type | competitor_count | competitor_1_rank | competitor_2_rank | competitor_3_rank | client_rank | cluster | gap_value_score | action_required | content_exists | priority_tier | notes
```

### Keyword Gap Report Template
```markdown
# Keyword Gap Report — [Client Name]
**Date:** YYYY-MM-DD
**Competitors Analyzed:** [domains]
**Total Gap Keywords Identified:** X
**Total Missing Traffic Potential:** X visits/mo (if ranked #1)

## Gap Summary by Type
| Gap Type | Keyword Count | Total Volume | Avg KD | Priority |
|---|---|---|---|---|
| Full Gap | | | | |
| Partial Gap | | | | |
| Ranking Gap | | | | |

## Top 10 Priority Clusters
| Cluster | Volume | KD | Intent | Gap Type | Gap Value Score | Action |
|---|---|---|---|---|---|---|

## Quick Wins (30-day opportunities)
| Keyword | Volume | KD | Current Rank | Client Page | Action |
|---|---|---|---|---|---|

## Defensive Keyword Alerts
| Keyword | Client Rank | New Competitor Entering | Action |
|---|---|---|---|

## Content Calendar Mapping
| Quarter | Clusters | Estimated Pages | Expected Traffic Gain |
|---|---|---|---|

## Gap Closure Baseline
- Total trackable gap keywords: X
- Currently in top 20: X (X%)
- Target in 90 days: X (X%)
```

---

## Prioritization Framework

Sequence content production from gap analysis in this order:

1. **Ranking Gaps with High Volume** — client has a page, it's close (rank 11–20) → fastest traffic gain with least new content
2. **Full Gaps with Transactional Intent + Low KD** — no page exists, clear intent, low competition → new service/landing pages
3. **Full Gaps owned by all 4+ competitors** — highly validated demand, high competitor count = proven topic → worth content investment
4. **Partial Gaps on core service topics** — client's most important pages are underperforming vs. competitors → optimization + expansion
5. **Awareness Full Gaps** — TOFU content for long-term authority building; important but last in queue for revenue-focused engagements

**Hard rule:** Never create content to fill a gap just because a competitor ranks for it. The keyword must pass: (a) volume > 30/mo, (b) intent aligns with client's business model, (c) KD is achievable given client's DR. If all three aren't met, skip it.
