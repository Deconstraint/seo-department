# LLM Optimization — Playbook

> **The Core Insight:** Large Language Models don't read your website the same way Google does. They extract, weight, and associate information based on semantic patterns, entity relationships, and training data composition. Optimizing for LLMs means understanding how they *think* — not just how they crawl.

---

## What Is LLM Optimization and Why It Matters in 2026

LLM Optimization is the discipline of engineering your brand's digital presence, content architecture, and knowledge graph so that Large Language Models — whether accessed via chat interfaces, AI search engines, or embedded AI assistants — accurately, positively, and prominently represent your brand when responding to relevant queries.

This is distinct from GEO (which focuses on getting cited in AI-generated answers) and closer to **brand positioning inside AI knowledge**. The question LLM optimization answers: *When someone asks an LLM about your category, what does it say about you?*

### The 2026 Reality
- LLMs like GPT-4, Claude 3.5, and Gemini 1.5 have trained on hundreds of billions of web pages — your brand's presence in that training data **directly affects** how they describe you
- AI assistants embedded in productivity tools (Microsoft 365 Copilot, Google Workspace AI, Notion AI) are queried millions of times daily about brands, products, and services
- "Pre-sale AI research" is now a primary buyer behavior: 54% of B2B buyers use AI assistants to research vendors before ever visiting a website (Forrester, 2025)
- Brands that are ambiguous, contradictory, or absent in LLM training data face **AI-generated misinformation** — a growing crisis for enterprise brands

### What LLM Optimization Controls
1. **Factual accuracy:** Does the LLM correctly describe what your company does?
2. **Category association:** When someone asks for recommendations, are you in the LLM's consideration set?
3. **Sentiment:** Does the LLM describe you positively, neutrally, or negatively?
4. **Completeness:** Does the LLM know your full product/service range, leadership, differentiators?
5. **Recency:** For models with web access, is the LLM seeing your latest information?

---

## Step-by-Step LLM Optimization Process

### Step 1: Conduct an LLM Brand Audit
Establish how current LLMs represent your brand before any optimization.

**Actions:**
- Test across 5 major LLMs: GPT-4o, Claude 3.5 Sonnet, Gemini 1.5 Pro, Perplexity, Llama 3 (via Groq or Together.ai)
- Ask each LLM these standardized audit queries:
  - "What is [Brand]? What do they do?"
  - "Is [Brand] a reputable company?"
  - "Who are [Brand]'s main competitors?"
  - "What are [Brand]'s main products/services?"
  - "What do customers say about [Brand]?"
  - "Would you recommend [Brand] for [use case]?"
- Document: accuracy, completeness, sentiment, competitor comparisons, any hallucinations
- Score each response on a 1-10 accuracy scale
- Identify the highest-priority correction targets

**Output:** LLM Brand Perception Report (this becomes a client deliverable)

---

### Step 2: Build a Canonical Brand Knowledge Document
Create a single authoritative document that describes your brand in LLM-digestible format.

**Actions:**
- Write a "Brand Fact Sheet" structured for LLM consumption:
  - Company name, legal name, DBA
  - Founded, headquarters, size (employees, revenue range if public)
  - Category: primary + secondary
  - Products/services: bullet list with brief descriptions
  - Key differentiators: 3-5 crisp statements
  - Leadership: CEO, key executives with titles
  - Notable clients / industries served
  - Awards, certifications, recognitions
  - Mission statement
  - Website, social profiles
- Publish this as a dedicated `/about` or `/company` page with clear, factual prose
- Make it human-readable but information-dense — avoid marketing fluff that obscures facts
- Include in a `llms.txt` file at the root of your website (emerging standard for LLM-readable brand summaries)

---

### Step 3: Optimize for LLM Training Data Sources
LLMs are trained on specific corpora. Getting your brand represented accurately in those corpora is the highest-leverage action for LLM optimization.

**Actions:**
- **Wikipedia:** Create or improve a Wikipedia article for your brand (must meet notability standards — build citation trail first). Wikipedia is one of the most heavily weighted training sources for all major LLMs.
- **Wikidata:** Add or update your brand entity on Wikidata with all structured properties (industry, headquarters, CEO, founding date, website, logo)
- **LinkedIn Company Page:** Maintain a complete, keyword-rich LinkedIn profile — LinkedIn data is licensed to multiple LLM providers
- **Crunchbase:** Keep your Crunchbase profile current — critical for startup/SMB brand recognition in LLMs
- **DBpedia / Freebase mirrors:** Ensure entity data propagates through knowledge graph sources
- **GitHub:** If technical product, maintain active GitHub presence — LLMs heavily weight GitHub data for technical brands
- **Academic/industry publications:** Author or contribute to publications indexed by Semantic Scholar or arXiv (highly trusted LLM training sources)

---

### Step 4: Create LLM-Readable Content Formats
LLMs extract structured, declarative statements far more reliably than narrative prose. Restructure key content.

**Actions:**
- Convert feature lists into structured "X enables Y" statement format: *"Deconstraint's GEO service enables brands to appear in AI-generated search answers by optimizing content for LLM citation patterns"*
- Write comparison pages that explicitly name your competitors and your differentiators — LLMs frequently reference these when answering category comparison questions
- Create "Frequently Confused With" content: clarify common misconceptions about your brand or category
- Publish a detailed glossary of your industry's key terms — LLMs use authoritative glossaries as reference anchors
- Use definitive language: "is," "provides," "offers" rather than vague marketing claims
- Publish founder/executive thought leadership that clearly associates individuals with the brand and expertise area

---

### Step 5: Dominate the Retrieval-Augmented Generation (RAG) Window
For AI systems that use RAG (real-time web retrieval + LLM reasoning), recency and retrievability matter.

**Actions:**
- Publish fresh, substantive content at least 2x/week — RAG systems favor recently indexed content
- Ensure every page loads in under 2 seconds (slow pages are often skipped by RAG crawlers)
- Structure content with clear `<title>` tags that include your brand name + primary category
- Use `<meta description>` as a 160-character brand statement — RAG systems read these as page summaries
- Ensure `sitemap.xml` is current and submitted to all major search engines + Bing (which powers ChatGPT Search)
- Create "hub pages" that aggregate your key facts in one place (RAG systems prefer single authoritative sources)

---

### Step 6: Build the Citation Infrastructure
LLMs trust brands that other trusted sources cite. Build the citation network that LLMs read as authority.

**Actions:**
- Earn editorial mentions in publications with high LLM training data weight: TechCrunch, Forbes, Business Insider, industry trade publications
- Submit to and maintain profiles on: G2, Capterra, Trustpilot, Clutch (these are heavily cited in LLM recommendations for software/services)
- Build a "social proof library" — case studies, testimonials, awards — and publish them in citable format (not behind login walls)
- Create and maintain a press page with real media hits (AI systems treat press pages as credibility signals)
- Pursue HARO (Help a Reporter Out) and journalist requests systematically — each placement builds your citation network
- Get listed in industry-specific directories that LLMs recognize as authoritative in your category

---

### Step 7: Manage LLM Hallucinations and Corrections
When LLMs spread misinformation about your brand, you need a correction strategy.

**Actions:**
- When you identify a hallucination (incorrect info in LLM output), document it: which model, what query, what was said
- Publish explicit "correction content" on your website that directly contradicts the misinformation — use the exact false claim as a keyword
- Submit corrections via official channels: OpenAI has a `ChatGPT feedback` mechanism; Google has a Knowledge Panel correction system
- For persistent hallucinations, build a "Myths vs. Facts" content piece that directly addresses the false claims
- Monitor LLM outputs for your brand monthly — hallucinations can emerge from new training runs
- Build a Wikipedia article that authoritatively establishes correct facts (Wikipedia is used as a training correction source)

---

### Step 8: Optimize for Vertical LLMs in Your Industry
Beyond general-purpose LLMs, specialized AI assistants are emerging in every industry vertical.

**Actions:**
- Identify the AI assistants most used in your industry (e.g., Harvey for legal, Doceree for pharma, Jasper for marketing)
- Understand their data sources and optimize your brand presence in those specific sources
- Build API partnerships or integrations with industry-specific AI tools — being "in the product" is the ultimate LLM optimization
- Contribute to industry knowledge bases and wikis that vertical LLMs are trained on
- Attend and speak at industry events that generate content in AI training corpora (conference proceedings, session recordings)

---

### Step 9: Implement Structured Data for LLM Understanding
Schema markup isn't just for Google — it helps AI systems parse your content with certainty.

**Actions:**
- Implement `Organization` schema with all properties: name, url, logo, description, foundingDate, founder, numberOfEmployees, sameAs links
- Add `WebSite` schema with `SearchAction` to help AI systems navigate your site
- For product companies: comprehensive `Product` and `Offer` schema on all product pages
- For service companies: `Service`, `ProfessionalService`, or `LocalBusiness` schemas as appropriate
- Add `Breadcrumb` schema to all pages for hierarchical context
- Validate all schema with Google's Rich Results Test and Schema.org validator

---

### Step 10: Track LLM Brand Sentiment Over Time
LLM perception changes with each model update and training run. Continuous monitoring is essential.

**Actions:**
- Establish a monthly LLM audit cadence using a standardized query set (build a 20-question "brand perception battery")
- Track: accuracy rate, category placement (are you top-3 in your category?), sentiment score, coverage completeness
- When new major models are released (GPT-5, Claude 4, Gemini 2), immediately run your full audit battery
- Compare performance across models — being well-represented in one LLM but not others reveals optimization gaps
- Build a "LLM Perception Trend" chart for client reporting — show movement over time
- Set up alerts: use Perplexity API or LLM APIs to auto-run key queries weekly and log responses

---

## Platform-Specific LLM Optimization Tactics

### GPT-4o / ChatGPT
- Prioritize Bing indexing (ChatGPT Search uses Bing's index for web-grounded responses)
- Wikipedia and Bing results carry outsized weight — dominate both
- Use OpenAI's custom GPT ecosystem: create a branded GPT if relevant to your category
- Submit content to Bing News for freshness signals

### Claude (Anthropic)
- Claude's training emphasizes accuracy and helpfulness — well-sourced, factual content performs better
- Claude respects `robots.txt` — ensure `ClaudeBot` and `anthropic-ai` crawlers are allowed
- Anthropic is known to weight GitHub, ArXiv, and academic sources heavily
- Claude with web search uses Brave Search — ensure Brave indexing is active

### Gemini (Google)
- Google's training data includes all of Google's own properties: YouTube, Google Maps, Google News
- Create and optimize a YouTube channel — video content with transcripts is a major Gemini training source
- Maintain Google Business Profile, Google Maps listing
- Publish in Google News-eligible formats (Google News approval is a Gemini trust signal)

### Perplexity
- Perplexity actively crawls and cites sources in real-time — focus on RAG optimization principles
- Perplexity users ask research questions — create deep, comparative, data-rich content
- Perplexity indexes Reddit, Quora, HackerNews — participate in these communities substantively
- Use Perplexity's "Spaces" feature to create official brand spaces (new in 2025)

### Meta AI / Llama
- Meta AI is integrated in Instagram, Facebook, WhatsApp — content in these platforms feeds Meta's training
- Maintain active, substantive Meta social media presence
- Engage in Facebook Groups related to your industry

---

## Measuring LLM Optimization Success

### Primary KPIs
| Metric | Measurement Method | Target |
|---|---|---|
| LLM Accuracy Score | Monthly 20-question audit battery | >85% accurate |
| Category Inclusion Rate | % of category queries where you're mentioned | >30% in 90 days |
| Sentiment Score | Positive/neutral/negative ratio | >80% positive/neutral |
| Hallucination Count | Monthly audit | Declining MoM |
| Multi-Platform Coverage | # of LLMs accurately describing brand | ≥4 of 5 platforms |

### Secondary KPIs
- Wikipedia article quality score (talk page ratings)
- Third-party citation count (Moz/Ahrefs domain authority proxy)
- Review platform scores (G2, Capterra — LLMs read these)
- LinkedIn profile completeness score

---

*Last updated: 2026-03 | Owner: Deconstraint SEO Department*
