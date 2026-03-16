# Brand Mentions Playbook

> **Tactic:** Unlinked Brand Mention Reclamation
> **Difficulty:** Low | **Scalability:** Medium | **Link Quality:** High
> **Time to First Link:** 1–2 weeks per placement (fastest tactic in link building)

---

## 1. When to Use This Tactic

Use Brand Mentions when:
- The client already has brand recognition — people are writing about them but not always linking
- You want fast wins with minimal effort (these are warm, already-earned mentions)
- You need to improve link velocity without creating new content or doing heavy outreach
- The client has PR activity, product reviews, press mentions, or media coverage
- You want to start a new client engagement with immediate results while longer-term tactics ramp up

**Why it works:** When someone mentions a brand by name, they've already established the context for a link. Converting an unlinked mention to a linked one is the path of least resistance in all of link building — you're not asking for something they haven't already given you attention for.

**Best use cases:**
- Established brands with 6+ months of online presence
- Clients who've had PR campaigns, product launches, or media interviews
- Companies that appear in "best of" lists without hyperlinks
- Brands referenced in competitor comparisons
- Client content cited in articles without attribution links

**Do NOT use Brand Mentions when:**
- The client is brand new with no online presence (nothing to find)
- The client's brand name is a common generic word (impossible to separate mentions from noise)
- The site mentioning the brand is of very low quality (no point converting a spammy mention to a link)

---

## 2. Prospecting Criteria & Qualification Framework

### Mention Qualification Checklist
For each unlinked mention found, evaluate:
- [ ] **Publication quality:** DR ≥ 30 and organic traffic ≥ 500/mo
- [ ] **Context:** Is the brand mention positive or neutral? (Negative mentions don't get link requests)
- [ ] **Reachability:** Can we find an email contact for the author or editor?
- [ ] **Linkability:** Does the article already link out to other external sources? (Confirms they link)
- [ ] **Brand specificity:** Is the mention clearly about THIS client brand (not a generic word match)?
- [ ] **No existing link:** Confirm there's no link already by inspecting the anchor text in the article source
- [ ] **Link target:** Is there an obvious page on the client's site the link should point to? (Homepage, product page, or referenced content)

### Mention Types and Priority
| Mention Type | Priority | Notes |
|---|---|---|
| News article with named brand | High | Journalist should have linked originally |
| "Best [niche] tools" list mentioning brand | Very High | Easy ask — they're recommending the brand |
| Product review without link | High | Natural to link to product page |
| Competitor comparison mentioning brand | High | Context strongly implies a link |
| Academic or research citation | Very High | Scholarly credibility + do-follow often |
| Blog post "pro tip" or casual mention | Medium | Lower DR but still convertible |
| Social media (Twitter, Reddit, LinkedIn) | Low | No SEO value from social links, but good for brand monitoring |

### Prospecting Methods

**Method 1: Google Alerts (Passive Monitoring)**
- Set up Google Alerts for:
  - `"[exact brand name]"`
  - `"[brand name]" + "[product name]"`
  - `"[founder name]" + "[company name]"`
  - `"[brand name]" + "[main keyword]"`
- Set frequency: "As it happens" for large brands; "Once a day" for smaller brands
- Delivery: Google Alerts → your email or Slack (via Zapier)

**Method 2: Ahrefs Content Explorer (Historical Mining)**
1. Open Ahrefs Content Explorer
2. Search: `"[brand name]"` (with quotes for exact match)
3. Filter: Published date → "All time" (for first run); then "Last 30 days" for ongoing
4. Filter: Do-follow mentions OFF (or check manually — Content Explorer shows unlinked mentions)
5. Filter: DR ≥ 30, Traffic ≥ 500
6. Export the list — this gives you every indexed article mentioning the brand
7. Sort by DR descending — tackle highest-authority mentions first

**Method 3: Google Search Mining**
```
"[brand name]" -site:[clientdomain.com]
"[brand name]" "top [niche] tools"
"[brand name]" "alternative to"
"[brand name]" "[year]" -site:[clientdomain.com]
"[brand name]" "review" -site:[clientdomain.com]
"[brand name]" "vs" -site:[clientdomain.com]
```
- Click through each result and check whether the brand name is hyperlinked
- Use "Find" (Ctrl+F) on the page to locate the brand mention quickly

**Method 4: Brand24 / Mention.com (Ongoing Monitoring)**
- Set up a Brand24 or Mention.com project for the client
- Configure keyword tracking: brand name, product names, founder names
- Set DR threshold filter: only notify for mentions on DR 30+ sites
- Review weekly and flag unlinked mentions for outreach

**Method 5: Semrush Brand Monitoring Tool**
- Semrush → .Trends → Brand Monitoring
- Enter brand name and competitors
- Filter by "No Link" to surface unlinked mentions specifically
- Export and prioritize by authority

---

## 3. Step-by-Step Outreach Process

### Phase 1: Research & Prospect Building (Days 1–3)

**Step 1: Conduct Historical Mention Audit**
- Use Ahrefs Content Explorer + Google Search methods above
- Mine ALL mentions from the past 12–24 months
- Build a master list in Google Sheets or Airtable
- Log: page URL, domain, DR, traffic, article date, mention context, existing link (yes/no), contact email

**Step 2: Qualify and Prioritize Prospects**
- Remove: DR < 30 / traffic < 500 / negative sentiment / brand already linked / no contact available
- Score remaining by DR (highest first)
- Separate into batches: Tier 1 (DR 70+), Tier 2 (DR 50–70), Tier 3 (DR 30–50)
- Target Tier 1 first — highest value, and the "quick win" frame is strongest on big publications

**Step 3: Find Contact Information**
- Find the author's email (not the general contact form — find the specific writer)
- Sources: Muck Rack byline email, author bio page, Hunter.io, LinkedIn
- If no author email: use editorial contact (editor@domain.com or submissions@domain.com)
- Verify all emails with NeverBounce before sending

**Step 4: Identify the Right Link Target**
- For each mention, determine the best URL on the client's site to link to:
  - Brand mention in general context → Homepage or About page
  - Product/feature mention → Product page or landing page
  - Study/data cited → The actual research page/blog post
  - "Best of" list → Homepage or most relevant product page
  - Review mention → Product page or pricing page
- Note this target URL in your tracking sheet — include it in your outreach

### Phase 2: Outreach (Days 3–10)

**Step 5: Craft Personalized Outreach Emails**
- Keep each email short (under 100 words) — this is the simplest ask in link building
- Thank the author genuinely before making the ask
- Reference the specific article and the specific mention
- Make the link request feel natural — frame it as "helpful for your readers" not "SEO for us"
- Suggest the exact URL to link to (makes it easy for the editor to act)

**Step 6: Send Initial Emails**
- Send in batches of 20–30/day per sending domain
- Best send times: Tuesday–Thursday, 9–11 AM
- Use a tracking tool (Lemlist, Mailshake, or Yesware) to monitor opens and replies
- Send Tier 1 emails manually with full personalization; Tier 2–3 can use lightweight templates

**Step 7: Follow Up**
- Follow-up #1: Day 4–5 (brief bump if no response)
- Follow-up #2: Day 9–10 (final attempt)
- Do NOT send more than 3 touches per prospect
- If a mention is from a major publication (Forbes, NYT), follow up only once — over-contacting premium journalists burns future opportunities

**Step 8: Handle Replies**
- "Sure, added it!" → Thank them, verify the link is live and correct, log in tracker
- "We don't add links after publication" → Note the policy, move on; don't push
- "Can you send the URL?" → Provide it immediately with a note on why it's relevant
- No reply after 3 touches → Mark exhausted; move on

### Phase 3: Verification & Ongoing Monitoring (Ongoing)

**Step 9: Verify Every Converted Mention**
- Visit the article page and confirm: link is present, do-follow, and pointing to correct URL
- Run the URL through Ahrefs to confirm the backlink appears in the index
- Log confirmation in your tracking sheet with date live and anchor text

**Step 10: Set Up Ongoing Monitoring**
- Configure Brand24, Google Alerts, or Ahrefs Alerts for continuous monitoring
- Review weekly for new unlinked mentions
- Process new mentions within 7 days for highest conversion rate (the article is still fresh; author is still active)
- Add the alert workflow to a recurring task in your project management system

---

## 4. Outreach Email Templates

### Template A: Standard Mention Conversion (Article / Blog Post)

**Subject:** Your mention of [Brand] in "[Article Title]"

Hi [First Name],

Thank you for mentioning [Brand] in your recent article — really appreciate the inclusion.

I wanted to make a quick ask: would it be possible to add a hyperlink to the mention? The URL is [target URL]. It would make it easy for your readers to visit [Brand] directly.

Totally understand if not — just wanted to flag it.

[Your Name]
[Title] | [Company]

---

### Template B: "Best Of" List / Roundup Mention

**Subject:** [Brand] mention in your [Topic] roundup

Hi [First Name],

Thanks so much for including [Brand] in your list of [what the list covers] — really glad it made the cut.

One quick note: we noticed the mention isn't hyperlinked. Would you be able to add a link to [URL]? It would help your readers learn more about [Brand] directly.

Thanks again for the feature — great resource you've built.

[Your Name]

---

### Template C: Data / Study Cited Without Link

**Subject:** Attribution link for [Study/Data] cited in your article

Hi [First Name],

Thanks for referencing [Brand]'s [study/data/report] in your piece on [article topic]. Really glad the data was useful.

Would you be open to adding a link back to the original research at [URL]? It helps readers access the full methodology and dataset.

[Your Name]
[Title] | [Brand]

---

### Template D: Product Review Without Link

**Subject:** Quick question about your [Brand] review

Hi [First Name],

Thank you for reviewing [Brand] — great feedback and we genuinely appreciate the coverage.

I noticed the review doesn't include a link to [Brand]'s website. Would it be possible to add one? [URL] goes directly to the [product page / homepage / pricing page] that would be most useful for your readers.

[Your Name]

---

### Template E: High-Authority Publication (Forbes, NYT, etc.) — Very Brief

**Subject:** [Brand] mention in your [Article Topic] piece

Hi [First Name],

Thanks for mentioning [Brand] in your recent [outlet] article. Just a quick note: the mention isn't currently linked. Would you be able to add a link to [URL]?

Really appreciate your work.

[Your Name]

---

### Template F: Follow-Up #1

**Subject:** Re: Your mention of [Brand] in "[Article Title]"

Hi [First Name],

Just wanted to follow up on my note about the [Brand] mention in case it got buried. Happy to provide any details that would help.

[Your Name]

---

## 5. Campaign Tracking & Management

### Master Tracking Spreadsheet Schema
| Field | Description |
|---|---|
| Article URL | Full URL of the article mentioning the brand |
| Domain | Root domain |
| DR | Domain Rating at time of contact |
| Traffic | Monthly organic traffic estimate |
| Article Date | When the article was published |
| Mention Context | Brief note on how brand was mentioned |
| Mention Type | News / Review / List / Comparison / Citation / Other |
| Author Name | Who wrote the article |
| Author Email | Verified email |
| Date Pitched | Initial send |
| Follow-up 1 | Date |
| Follow-up 2 | Date |
| Status | Found / Pitched / Replied / Converted / Declined / No Response |
| Link Live | Yes / No |
| Link URL | URL of client page being linked to |
| Anchor Text | What was used |
| Do-Follow? | Yes / No |
| Date Confirmed | When link went live |
| Notes | Special context |

### Weekly Workflow
- **Monday:** Pull new mentions from Brand24, Ahrefs Alerts, and Google Alerts
- **Tuesday:** Qualify and add new mentions to tracker; find contact emails
- **Wednesday:** Send outreach batch (new mentions + fresh prospects)
- **Thursday:** Follow up on Day-5 emails from previous week
- **Friday:** Verify all newly confirmed links; update statuses; pull reporting metrics

### Tools
- **Monitoring:** Brand24, Mention.com, Ahrefs Alerts, Google Alerts
- **Discovery:** Ahrefs Content Explorer, Semrush Brand Monitoring, Google Search Operators
- **Email Finding:** Hunter.io, Muck Rack, Apollo.io
- **Email Verification:** NeverBounce, ZeroBounce
- **Outreach:** Lemlist, Mailshake, or manual Gmail
- **Tracking:** Airtable or Google Sheets

---

## 6. Success Metrics & KPIs

### Primary KPIs
| Metric | Target |
|---|---|
| Unlinked mentions found per month | 10–50+ (varies by brand size) |
| Outreach-to-response rate | 25–40% (warm outreach converts well) |
| Response-to-conversion rate | 50–70% |
| Overall conversion rate (mention → live link) | 15–30% |
| Average DR of converted links | ≥ 45 |
| % Do-Follow | ≥ 75% |
| Time from outreach to confirmed link | < 10 days |

### Secondary KPIs
- Number of brand mentions being monitored (ongoing)
- % of new mentions processed within 7 days (freshness = higher conversion)
- Year-over-year growth in brand mention volume (more PR/content activity = more future opportunities)
- Referring domain growth rate
- Client domain rating improvement (60-day and 90-day tracking)

### Benchmarks by Brand Size
| Brand Stage | Monthly Unlinked Mentions | Monthly Convertible Links |
|---|---|---|
| Small / Emerging (< 1 year) | 5–15 | 1–5 |
| Established (1–3 years) | 15–50 | 5–15 |
| Mid-market (3+ years, some PR) | 50–200 | 15–50 |
| Enterprise / High PR activity | 200–1,000+ | 50–150 |

---

## 7. What to Avoid

### Outreach Mistakes
- **Sending a long, complex email to request a simple link** — This is the simplest ask in link building. Keep emails short. A 3-sentence email outperforms a 10-sentence one for this tactic.
- **Making the ask feel entitled** — "You mentioned us without linking, you should add the link" is the wrong tone. Frame it as a courtesy/request, not a demand.
- **Emailing the webmaster instead of the author** — Authors are far more likely to act on a link request for their own article. Find the author's email whenever possible.
- **Not specifying the exact URL** — Always give the editor the exact URL to link to. Friction = lost conversions.
- **Following up too aggressively on high-authority publications** — More than one follow-up to a Forbes or NYT journalist is likely to get you ignored or flagged as spam.

### Google & SEO Pitfalls
- **Requesting links from negative mentions** — A brand mention in a critical article is not a target. Linking can draw more attention to the negative coverage.
- **Over-optimizing anchor text requests** — If the mention says "Master Control Program" and you want the anchor to be "best AI assistant software," you've crossed into manipulation. Let the natural brand name be the anchor.
- **Converting mentions on low-quality sites** — A link from a spammy site is worse than no link. Stick to DR 30+ sites with real traffic.
- **Ignoring social mentions** — Social links don't pass SEO value, but they're worth tracking for brand awareness and can lead to future editorial mentions. Monitor but don't prioritize for link conversion.

### Operational Issues
- **Not setting up monitoring proactively** — Mentions age quickly. An article published 2 years ago is harder to get a link added to than one published 2 weeks ago. Set up real-time monitoring.
- **Letting the tracking sheet fall behind** — Untracked outreach leads to double-contacts, missed follow-ups, and inability to report results. Keep the tracker current daily.
- **Not celebrating wins with the client** — Brand mention conversions from DR 80+ publications are significant. Report these prominently — they build client confidence and demonstrate the tactic's value.
