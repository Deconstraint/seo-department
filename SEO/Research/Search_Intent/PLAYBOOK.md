# Search Intent — Playbook

## When to Use This

Use this playbook whenever you are mapping keywords to content types, diagnosing why a page isn't ranking despite strong on-page SEO, deciding what page type to create for a target keyword, auditing existing content for intent alignment, or briefing a content writer on angle and structure. Intent misalignment is the #1 reason well-optimized pages fail to rank — this playbook eliminates that failure mode.

---

## Step-by-Step Process

### Step 1: Pull the Keyword List
- [ ] Start with the Tier 1 keyword list from the Keyword Research playbook
- [ ] If auditing existing content: pull GSC data for all pages ranking 11–50, extract the primary query driving impressions for each page
- [ ] Group keywords into clusters before beginning intent analysis — intent is a cluster-level property, not just a keyword-level property
- [ ] Flag keywords where tool-reported intent (Ahrefs/Semrush) conflicts with gut instinct — these need manual SERP verification

### Step 2: Apply the Primary Intent Classification (AITO Model)
Classify every keyword using the **AITO Framework**:

| Intent Type | Definition | Behavioral Signal | Primary Goal |
|---|---|---|---|
| **Awareness** | User learning about a topic for the first time | "what is," "how does," "why," "explain" | Educate |
| **Investigation** | User comparing options, researching before deciding | "best," "vs," "review," "top," "alternative" | Help evaluate |
| **Transaction** | User ready to act (buy, hire, sign up, download) | "buy," "hire," "get," "near me," "cost," "price" | Convert |
| **Orientation** | User looking for a specific page/brand/location | Brand name, "login," "contact," "[company] [city]" | Navigate to destination |

- [ ] Classify every keyword into one of these 4 categories
- [ ] Document in the master sheet (column: `primary_intent`)
- [ ] For multi-intent keywords (e.g., "best CRM for small business" is Investigation but near-Transaction), flag as "blended intent" and identify the dominant signal from the SERP

### Step 3: Verify Intent Against the Live SERP
Never trust tool classifications alone. For every Tier 1 keyword:

- [ ] Run a live Google search (incognito, target geo)
- [ ] Look at the top 3 results: what page TYPE are they? (blog post, product page, comparison page, local service page, video, etc.)
- [ ] The page type Google rewards = the intent Google reads for that query
- [ ] If the SERP shows service pages but you classified the keyword as Awareness → reclassify as Transaction
- [ ] Record the **SERP-confirmed content type** as the ground truth (not your initial classification)

### Step 4: Map Intent to Content Type
For each keyword, determine the correct content type using this mapping:

| Intent | SERP-Confirmed Content Type | Template to Use |
|---|---|---|
| Awareness | Long-form blog post, guide, pillar page | Educational article template |
| Awareness | FAQ page | FAQ + schema template |
| Investigation | Comparison page | "Best X" or "X vs Y" template |
| Investigation | Review / roundup | Listicle template with structured data |
| Transaction | Service page | Service page template |
| Transaction | Product page | Product + schema template |
| Transaction | Local landing page | Local SEO template |
| Orientation | Homepage, About, Contact, Login | Existing page — optimize, don't replace |

- [ ] Assign a content template to each keyword cluster
- [ ] Flag any existing client pages where the page type does NOT match this mapping → high-priority rework

### Step 5: Sub-Intent Extraction (Micro-Intent Mining)
Every primary keyword has sub-intents — secondary questions users have while in that state of mind:

- [ ] For each keyword, collect the People Also Ask questions from the SERP (use SERP Analysis playbook PAA step)
- [ ] Collect the "Related searches" at the bottom of the SERP
- [ ] Run the keyword through Ahrefs → "Questions" filter in Keyword Explorer → export all questions with volume
- [ ] Group questions by sub-topic: these become your H2/H3 headings in the content brief

**Example:**
- Primary keyword: "best CRM for small business" (Investigation)
- Sub-intents: "free CRM for small business," "CRM with Gmail integration," "simple CRM no training needed," "CRM pricing comparison"
- These sub-intents = section headings in the comparison article

### Step 6: Funnel Stage Mapping
Map each keyword cluster to a funnel stage for content strategy alignment:

| Funnel Stage | Intent Match | Primary Metric | CTAs to Use |
|---|---|---|---|
| **TOFU** (Top of Funnel) | Awareness | Organic traffic, time on page | Newsletter, content upgrade, free resource |
| **MOFU** (Middle of Funnel) | Investigation | Pages per session, demo requests, lead magnet | Case study, free trial, comparison |
| **BOFU** (Bottom of Funnel) | Transaction | Conversions, form submissions, calls | "Get a quote," "Book a call," "Buy now" |

- [ ] Tag each keyword cluster with: `TOFU`, `MOFU`, or `BOFU`
- [ ] Ensure client's content calendar has balanced distribution — pure TOFU content doesn't convert; pure BOFU is hard to rank
- [ ] For new client engagements with no existing organic traffic: prioritize BOFU first (revenue impact), then build MOFU, then TOFU

### Step 7: Existing Content Intent Audit
Run this for every page on the client's site ranking in positions 11–50:

- [ ] Pull GSC: for each URL, what is the #1 query driving impressions?
- [ ] Classify that query's intent using AITO
- [ ] Compare intent to the actual page type: does the page match?
- [ ] If mismatch: document as "intent mismatch" → rework the page to match SERP-expected content type
- [ ] If match but still ranking poorly: check for other on-page or authority issues (refer to Technical and Link playbooks)

**Common Mismatches:**
- Blog post ranking for a transactional query → should be a service/product page
- Service page ranking for an informational query → Google doesn't want to show a sales page for "how to" queries
- Homepage targeting a specific keyword that should have its own dedicated landing page

### Step 8: Content Depth & Format Requirements
Based on confirmed intent, determine the required depth:

- [ ] **Awareness content:** Minimum 1,500 words; must answer the primary question in the first 200 words; use headers, images, and examples; include FAQ section at the end
- [ ] **Investigation content:** Minimum 2,000 words; use comparison tables; include pros/cons; score or rank the options; keep neutral tone (not overtly promotional)
- [ ] **Transaction content:** 500–1,500 words; lead with the offer and CTA; include trust signals (reviews, certifications, case studies); local SEO signals for local intent
- [ ] **Orientation content:** Match what already ranks; often just needs title/meta optimization, not a content rewrite

### Step 9: Structured Data Intent Alignment
Match schema markup to intent type:

| Intent | Recommended Schema |
|---|---|
| Awareness | `Article`, `HowTo`, `FAQPage` |
| Investigation | `ItemList`, `Review`, `Product` (for review pages) |
| Transaction | `LocalBusiness`, `Service`, `Product`, `Offer` |
| Orientation | `Organization`, `BreadcrumbList`, `SiteLinksSearchBox` |

- [ ] For each keyword cluster, note the required schema types
- [ ] Pass to Technical team for implementation

### Step 10: Intent Shift Monitoring (Ongoing)
Search intent can change — especially after Google algorithm updates:

- [ ] Set up monthly SERP spot-checks for all Tier 1 keywords: has the dominant content type changed?
- [ ] Use Semrush Position Tracking: monitor if client pages gain/lose positions after an algorithm update
- [ ] After any major Google update (Core Update, Helpful Content): re-run SERP intent verification for all tracked keywords
- [ ] Log any intent shifts in the client's research folder — they may require content refreshes

---

## Frameworks & Models

### AITO Intent Framework
Awareness / Investigation / Transaction / Orientation — the four-state model of search behavior. More nuanced than the standard "navigational / informational / transactional" model because it separates passive awareness from active investigation.

### Funnel Stage Mapping (TOFU/MOFU/BOFU)
Links intent to the buyer journey. Ensures content strategy serves revenue goals, not just traffic goals.

### Content-Intent Fit Score
Rate each existing client page on a 1–5 scale:
- 5 = Page type perfectly matches SERP intent, content depth matches competitors, structured data present
- 3 = Page type matches but depth is insufficient, or structured data missing
- 1 = Clear intent mismatch — page type is wrong for what Google wants to rank

Pages scoring 1–2 are highest-priority for rework.

### Micro-Intent Matrix
| Primary Keyword | Primary Intent | Sub-Intent 1 | Sub-Intent 2 | Sub-Intent 3 |
|---|---|---|---|---|

Fill this in for every cluster — it becomes the content brief skeleton.

---

## Tools & Specific Instructions

### Ahrefs
- **Keyword Explorer → Questions filter:** Enter seed term → filter "Questions" → export all with volume > 10 → these are sub-intent signals
- **SERP Overview → "Position" tab:** Check what types of pages (service, blog, video) dominate for each keyword
- **Traffic Share by Pages:** Site Explorer → Organic Keywords → group by page to see which of client's pages attract which intent types

### Semrush
- **Keyword Overview → Intent column:** Semrush auto-classifies intent (informational/commercial/transactional/navigational) — use as a first pass, verify with SERP
- **Keyword Magic Tool → Intent filter:** Filter your keyword list by intent type to quickly segment
- **Topic Research:** Enter seed → generates content ideas organized by intent and engagement

### Google Search Console
- Performance → Pages → click any page → filter by query → find the primary driving query for each URL
- This reveals the true search intent Google is already associating with the page (may differ from your target keyword)

### AlsoAsked.com
- Free tool: enter any keyword → get a visual PAA tree showing all sub-intent questions Google surfaces
- Export as CSV → use to populate micro-intent matrix
- Use for content brief H2/H3 structure

### Google NLP API (Advanced)
- Submit the text of top-ranking pages to the Natural Language API → extract entities and categories
- Use to understand what semantic entities Google associates with a given intent
- Compare against client's existing content for entity coverage gaps

---

## Documentation & Storage

### File Structure
```
/SEO/Research/Search_Intent/
  PLAYBOOK.md
  [client-slug]/
    intent_maps/
      intent_classification_YYYY-MM-DD.csv
      content_intent_audit_YYYY-MM-DD.csv
    reports/
      Intent_Alignment_Report_[client]_YYYY-MM-DD.md
```

### Intent Classification Sheet Columns
```
keyword | cluster | primary_intent | SERP_confirmed_content_type | funnel_stage | content_depth_required | schema_type | content_intent_fit_score | action_required | notes
```

### Intent Alignment Report Template
```markdown
# Search Intent Alignment Report — [Client Name]
**Date:** YYYY-MM-DD

## Intent Distribution
- Awareness keywords: X (X%)
- Investigation keywords: X (X%)
- Transaction keywords: X (X%)
- Orientation keywords: X (X%)

## Intent Mismatch Pages (Priority Rework)
| Page URL | Current Type | Required Type | Primary Query | Action |
|---|---|---|---|---|

## New Content Required by Intent
| Cluster | Intent | Content Type | Funnel Stage | Priority |
|---|---|---|---|---|

## Schema Gaps
| Page | Required Schema | Status |
|---|---|---|
```

---

## Prioritization Framework

1. **Intent mismatches on existing pages** — fix first; these are pages already getting impressions but not ranking because the page type is wrong
2. **BOFU transactional gaps** — highest revenue impact; if client has no service pages for their core transactional keywords, create them before any TOFU content
3. **MOFU investigation content** — high-value middle stage; comparison and "best of" content captures users closest to buying
4. **TOFU awareness content** — important for authority building but lowest short-term conversion value; deprioritize for clients needing quick wins
5. **PAA and FAQ schema** — quick wins that can be applied to existing content without a full rewrite
