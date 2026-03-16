# SERP Analysis — Playbook

## When to Use This

Run SERP analysis before writing any piece of content, before optimizing an existing page, when a page is ranking but not converting, when a featured snippet or PAA box exists for a target keyword, or when a client's rankings drop unexpectedly. SERP analysis tells you *what Google wants* for a given query — ignore it and you're guessing.

---

## Step-by-Step Process

### Step 1: Define the Target Keyword Set
- [ ] Pull the Tier 1 keyword list from the Keyword Research playbook output
- [ ] For each keyword you plan to analyze, confirm it has a stable search volume (not seasonal spike) — check Ahrefs "Volume History" graph
- [ ] Group keywords by cluster — analyze all keywords in a cluster together, not one-off
- [ ] Prioritize clusters where the client has existing content ranking 11–50 (optimization opportunity) over net-new content

### Step 2: SERP Feature Mapping
For each target keyword, run a live Google search (use incognito + target geo if local SEO) and document every SERP feature present:

- [ ] **Ads:** How many ads at top? How many at bottom? (signals commercial intent and competition)
- [ ] **Featured Snippet:** Type — paragraph, list, table, video? Who owns it?
- [ ] **People Also Ask (PAA):** List all visible PAA questions — these are sub-intent signals
- [ ] **Local Pack:** Is a 3-pack present? (critical for local clients)
- [ ] **Image Pack / Video Carousel:** Note position and triggering intent
- [ ] **Sitelinks:** Does any result have sitelinks? (indicates dominant brand presence)
- [ ] **Knowledge Panel:** Is there an entity card? (signals informational/navigational intent)
- [ ] **Shopping Results:** Present? (means strong transactional intent)
- [ ] **Top Stories / News:** Present? (signals freshness requirement — content must be updated regularly)

Use the **SERP Feature Scoring Sheet** (see Documentation section) to record all features per keyword.

### Step 3: Competitor Content Audit (Top 10 Analysis)
For each target keyword, analyze the top 10 organic results:

- [ ] Record: URL, domain, page title, meta description, estimated word count (use Ahrefs Content Gap or SEOquake), DR of domain
- [ ] Identify the **dominant content format**: long-form guide, listicle, service page, product page, video, tool/calculator
- [ ] Note **content freshness**: publication date and last modified date (visible in SERP or in page source)
- [ ] Check **E-E-A-T signals**: author bio, credentials listed, citations, data sources, About page quality
- [ ] Flag any result that is a weaker-than-expected domain ranking above stronger domains — this indicates a content quality edge exists

### Step 4: Content Gap & Depth Analysis
- [ ] Open top 3 ranking pages for each keyword
- [ ] Use Ahrefs "Content Gap" or manually audit: what H2/H3 sections do they cover?
- [ ] Create a **content outline skeleton** for each keyword based on what the top 3 cover, noting what each covers that others miss
- [ ] Identify: what question does this page need to answer that no current top-10 result answers completely? This is your differentiator angle.
- [ ] Use Semrush **SEO Content Template**: enter keyword → get LSI terms, recommended word count, readability target, and backlink suggestions from top 10

### Step 5: Dominant Intent Determination
Use the **4D Intent Model** to confirm the dominant intent signal from the SERP:

| Dimension | What to Observe | Interpretation |
|---|---|---|
| **Domain** | .com service pages vs. blogs vs. .gov | Service pages = transactional; blogs = informational |
| **Depth** | Word count of top 3 results | Short = quick answer; long = research intent |
| **Design** | Page layout (landing page vs. article vs. tool) | Landing page = conversion intent; article = educational |
| **Diversity** | How varied are the result types? | High diversity = ambiguous intent; low = clear intent |

- [ ] Record dominant intent classification for each keyword in the master SERP analysis sheet
- [ ] If intent conflicts with the content currently on the client's page → flag for content type mismatch (major ranking factor)

### Step 6: Title Tag & Meta Description Pattern Analysis
- [ ] For each keyword, collect all 10 title tags from the SERP
- [ ] Identify common patterns: do titles include the exact keyword? Do they use numbers ("7 Best...")? Questions ("How to...")? Power words ("Ultimate," "Complete," "Expert")?
- [ ] Note character length of top-3 titles — Google typically displays ~60 chars
- [ ] Collect all 10 meta descriptions — note which ones include CTAs, social proof, or urgency signals
- [ ] Draft 2–3 title tag options for client's page that match the dominant pattern but differentiate

### Step 7: Featured Snippet Opportunity Assessment
- [ ] For keywords where a featured snippet exists: identify the format (paragraph/list/table) and the current snippet source
- [ ] Determine if the snippet is "ownable": DR of current snippet owner < client's DR + 10? → High opportunity
- [ ] For list snippets: the answer must be in a clean `<ul>` or `<ol>` with 6–8 items, the intro sentence must directly answer the query
- [ ] For paragraph snippets: 40–60 words, starts with a direct answer, uses the keyword in the first sentence
- [ ] For table snippets: use proper `<table>` HTML, include the keyword in the table caption or nearest H2

### Step 8: PAA Mining
- [ ] For each target keyword, click to expand all visible PAA boxes and record every question
- [ ] Expand secondary PAA questions (clicking one PAA generates 4 more) — capture at least 10–15 total
- [ ] Group PAA questions by sub-topic — these become FAQ sections or supporting H2/H3 headings in content
- [ ] Cross-reference PAA questions against the keyword cluster's spoke keywords — if a PAA question matches a spoke keyword, it's a strong content signal

### Step 9: Backlink Profile of Top Rankers
- [ ] In Ahrefs: check referring domains count for position 1, 3, 5, and 10 results for each target keyword
- [ ] Note: average referring domains needed to be competitive (this informs link building targets)
- [ ] Identify: does any top-5 result have significantly fewer referring domains than others? (weak link profile = content quality win)
- [ ] Flag anchor text patterns for the top result — are they exact match, partial match, or branded?

### Step 10: SERP Volatility Check
- [ ] In Ahrefs: check the "SERP History" for each target keyword — has the top 3 been stable for 6+ months, or is there churn?
- [ ] High volatility (frequent rank changes) = Google is unsatisfied with existing results → opportunity for a definitively better piece
- [ ] Check Semrush **Sensor** for overall SERP volatility in the client's niche on the analysis date
- [ ] Record volatility score: Stable (same top 3 for 6+ mo), Moderate (some churn), High (top 3 changed in last 30 days)

### Step 11: Synthesize & Prioritize
- [ ] Compile SERP analysis findings into the **SERP Analysis Report** (see Documentation)
- [ ] Flag "SERP-ready" keywords: featured snippet available, weak competitors, or intent mismatch on current client page
- [ ] Pass content format requirements and outline skeletons to Content team
- [ ] Pass backlink target counts to Link Building team

---

## Frameworks & Models

### SERP Feature Scoring
Rate each keyword's SERP "complexity" on a 1–5 scale:
- 1 = Clean organic results, no ads, no features
- 2 = Ads only or one minor feature (PAA)
- 3 = Multiple features, video or image pack
- 4 = Local pack + ads + PAA
- 5 = Shopping + knowledge panel + heavy ads (very hard to rank organically)

Lower SERP complexity = easier organic visibility.

### 4D Intent Model
Domain / Depth / Design / Diversity — see Step 5 above.

### Content Differentiation Matrix
For each keyword, score each top competitor on:
- Comprehensiveness (0–10): Does it cover all sub-topics?
- Freshness (0–10): How recently updated?
- E-E-A-T (0–10): Author credentials, citations, trust signals?
- UX (0–10): Load speed, readability, mobile-friendly?

Client's target score: beat the average of top 3 by at least 15%.

### Featured Snippet Eligibility Criteria
- Snippet currently exists: ✅ required
- Current snippet owner DR is within 20 points of client: ✅ required
- Content format is replicable: ✅ required
- Client can produce content within 2 weeks: ✅ required

All 4 must be met to classify as "featured snippet target."

---

## Tools & Specific Instructions

### Ahrefs
- **SERP Overview:** Keyword Explorer → search term → SERP tab → shows live positions, DR of each result, backlink counts, estimated traffic
- **SERP History:** Same page, scroll down → see historical position changes for each URL
- **Content Gap:** Site Explorer → client domain → Content Gap → enter competitor domains → find missing keywords

### Semrush
- **SEO Content Template:** Content → SEO Content Template → enter keyword + geo → get LSI terms, recommended length, backlink sources
- **Keyword Overview → SERP Features:** See which SERP features appear for any keyword
- **Position Tracking → SERP Features:** Monitor if client wins/loses featured snippets over time

### Google Search (Manual)
- Always use incognito mode for unbiased results
- For local keywords: append city name or use Google's location emulator (Search Console Inspection tool shows geo-specific SERP)
- Screenshot the full SERP for the record — use **GoFullPage** browser extension

### Screaming Frog
- Spider the top-10 competitor URLs for each keyword cluster
- Export: title, meta description, H1, word count, canonical, structured data
- Use for bulk title/meta pattern analysis

### SEOquake (Chrome Extension)
- Overlay DR, backlinks, indexed pages on SERP results in real-time
- Enable "Show SERP overlay" for instant competitive data without leaving Google

---

## Documentation & Storage

### File Structure
```
/SEO/Research/SERP_Analysis/
  PLAYBOOK.md
  [client-slug]/
    raw/
      serp_screenshots/
        [keyword-slug]_YYYY-MM-DD.png
      competitor_exports/
        top10_[keyword-cluster]_YYYY-MM-DD.csv
    processed/
      serp_analysis_master_YYYY-MM-DD.csv
    reports/
      SERP_Analysis_Report_[client]_YYYY-MM-DD.md
```

### SERP Analysis Master Sheet Columns
```
keyword | search_volume | SERP_complexity_score | dominant_intent | featured_snippet_exists | snippet_format | snippet_owner_DR | PAA_count | local_pack | ads_count | avg_DR_top10 | content_format | avg_wordcount_top3 | client_current_rank | opportunity_flag | notes
```

### SERP Analysis Report Template
```markdown
# SERP Analysis Report — [Client Name]
**Date:** YYYY-MM-DD
**Keywords Analyzed:** X
**Clusters Covered:** X

## Key Findings
- [Top 3 insights]

## Featured Snippet Opportunities
| Keyword | Current Owner | Client Gap | Format Needed |
|---|---|---|---|

## Content Format Requirements
| Cluster | Required Format | Min Word Count | E-E-A-T Requirement |
|---|---|---|---|

## Competitor Weaknesses Identified
| Competitor | Weakness | Keywords Affected |
|---|---|---|

## Recommended Actions
1. [Priority 1]
2. [Priority 2]
```

---

## Prioritization Framework

1. **Featured Snippet targets** — fastest wins, high visibility, can be captured without link building
2. **Intent mismatch pages** — client has a page ranking 11–30 but the page type doesn't match SERP intent → highest ROI optimization
3. **Weak competitor clusters** — top results have low DR or thin content → produce a definitively better asset
4. **PAA optimization** — add FAQ schema to existing content to win PAA boxes
5. **SERP volatility plays** — enter volatile SERPs with a fresh, high-quality piece while Google is still deciding

Never prioritize a keyword where the top 10 are all DA 80+ domains with 500+ referring domains — unless the client has matching authority or a very specific content edge.
