# Mobile SEO — Technical SEO Playbook

## When to Use This

Use this playbook when:
- A client's site is not mobile-friendly (Google's Mobile-Friendly Test fails)
- GSC shows "Mobile Usability" errors
- Mobile organic traffic is underperforming desktop (large gap suggests mobile UX issues)
- Core Web Vitals are poor specifically on mobile
- A site was designed desktop-first and hasn't been audited for mobile
- Google Search Console shows interstitial/pop-up warnings
- Text is flagged as too small to read or tap targets too close together
- After any major redesign that may have broken responsive behavior

---

## Why Mobile-First Indexing Matters

Google crawls and indexes the **mobile version** of a page. If your mobile site has less content, different structured data, or slower performance than desktop, Google indexes the mobile-degraded version.

- Mobile-first indexing: active for all sites since 2023
- If Googlebot sees different content on mobile vs desktop, mobile wins (and loses)
- Mobile Core Web Vitals data is what GSC reports for CWV ranking signals

---

## Step-by-Step Checklist

### 1. Run Google's Mobile-Friendly Test
- URL: `https://search.google.com/test/mobile-friendly`
- Enter each key page URL and screenshot results
- Look for: "Page is not mobile friendly" → list of specific issues
- Also run GSC > Experience > Mobile Usability for sitewide report

### 2. Verify Viewport Meta Tag is Present and Correct
This is the most fundamental mobile SEO requirement:
```html
<!-- CORRECT — responsive viewport -->
<meta name="viewport" content="width=device-width, initial-scale=1">

<!-- WRONG — fixed-width viewport (causes zoomed-out layout) -->
<meta name="viewport" content="width=640">

<!-- WRONG — disabling user zoom (accessibility issue + SEO signal) -->
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
```
Check every page template — missing viewport is often on non-standard page types (landing pages, custom templates).

### 3. Audit Responsive CSS Breakpoints
Using Chrome DevTools:
1. Open DevTools > Toggle device toolbar (Ctrl+Shift+M)
2. Test at: 375px (iPhone SE), 390px (iPhone 14), 412px (Android), 768px (tablet)
3. Check for: horizontal scrolling, overlapping elements, text overflow, broken navigation

Common CSS fixes:
```css
/* Prevent horizontal scroll */
body {
  overflow-x: hidden;
}

/* Responsive images */
img {
  max-width: 100%;
  height: auto;
}

/* Responsive tables */
table {
  width: 100%;
  overflow-x: auto;
  display: block;
}

/* Touch-friendly tap targets */
a, button {
  min-height: 44px;  /* Apple HIG minimum */
  min-width: 44px;
  padding: 12px;
}
```

### 4. Check Tap Target Size and Spacing
Google flags tap targets under 48x48px or spaced less than 8px apart.

GSC Mobile Usability > "Clickable elements too close together"

Fix:
```css
/* Ensure minimum tap targets */
.nav-link, .cta-button, .form-input {
  min-height: 48px;
  padding: 12px 16px;
}

/* Increase spacing between adjacent links in footer/nav */
.footer-link {
  margin: 8px 0;
  display: inline-block;
}
```

### 5. Verify Content Parity (Mobile vs Desktop)
Google indexes mobile content. If mobile shows less:
- Collapsed/hidden content (CSS `display:none` on mobile) **is still indexed**, but may be weighted less
- Tabs and accordions: content is indexed but may carry less weight
- Never hide meaningful content on mobile to "simplify" — this can hurt rankings

Check:
```bash
# Compare mobile vs desktop rendered content
# Use GSC > URL Inspection > Test Live URL > Screenshot (mobile)
# Compare to desktop screenshot

# Also test with Screaming Frog in mobile user-agent mode:
# Configuration > User-Agent > Googlebot Smartphone
```

### 6. Configure for Googlebot Smartphone Crawling
Googlebot uses two user-agents:
- Desktop: `Mozilla/5.0 ... Googlebot/2.1`
- Smartphone: `Mozilla/5.0 ... Mobile Safari... Googlebot/2.1`

Ensure server doesn't serve different content to mobile Googlebot:
```bash
# Test mobile Googlebot response
curl -H "User-Agent: Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/122.0.0.0 Mobile Safari/537.36 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)" https://domain.com/
```
Verify HTML content is identical (or better) than desktop response.

### 7. Eliminate Intrusive Interstitials
Google penalizes pages with intrusive pop-ups on mobile that block content before users see it.

**NOT allowed (SEO-penalized):**
- Full-screen pop-ups that appear immediately on page load
- Pop-ups that cover the main content and require dismissal to see page
- Standalone interstitials that must be dismissed before content is accessible

**Allowed:**
- Cookie consent banners (legal requirement)
- Age verification gates
- Login walls for private content
- Banners that use reasonable screen space (under ~20% viewport height)

Fix: Set pop-ups to trigger after user interaction (scroll, time on page) rather than on load, and ensure they don't cover main content area.

### 8. Optimize Mobile Page Speed
Mobile typically performs worse than desktop. Key mobile-specific optimizations:

```html
<!-- Preload LCP image for mobile viewport -->
<link rel="preload" as="image" 
  href="/hero-mobile.webp" 
  media="(max-width: 768px)"
  fetchpriority="high">

<!-- Serve smaller images for mobile -->
<img srcset="hero-mobile.webp 400w, hero-tablet.webp 800w, hero-desktop.webp 1200w"
     sizes="(max-width: 480px) 400px, (max-width: 900px) 800px, 1200px"
     src="hero-desktop.webp" alt="Hero">
```

Reduce JavaScript for mobile:
```javascript
// Conditionally load heavy features only on desktop
if (window.innerWidth > 768) {
  import('./desktop-only-feature.js');
}
```

### 9. Check for Mobile-Specific Structured Data
Structured data should be present on mobile version:
- If structured data is only in a JS component that doesn't render on mobile, Google won't see it
- Use GSC > URL Inspection > Test Live URL to verify structured data is present in mobile rendering
- Fix: Ensure structured data JSON-LD is in the base HTML, not injected after page load

### 10. Test Font Sizes and Readability
Google flags "Text too small to read" in Mobile Usability when base font size is < 12px.

```css
/* Minimum readable font sizes for mobile */
body {
  font-size: 16px;  /* Never go below 16px for body text */
  line-height: 1.6;
}

/* Scale headings appropriately */
h1 { font-size: clamp(1.5rem, 5vw, 2.5rem); }
h2 { font-size: clamp(1.25rem, 4vw, 2rem); }

/* NEVER do this */
p { font-size: 10px; }
.small-print { font-size: 11px; }
```

### 11. Validate AMP Pages (If Used)
If the site uses AMP (Accelerated Mobile Pages):
```bash
# Validate AMP HTML
npx amphtml-validator https://domain.com/amp-page/

# Or use online validator
# https://validator.ampproject.org/
```
- AMP pages must be canonical-linked from their non-AMP equivalent
- Non-AMP page should include: `<link rel="amphtml" href="https://domain.com/amp-page/">`
- AMP page should include: `<link rel="canonical" href="https://domain.com/page/">`

**Note:** AMP is largely deprecated for SEO purposes (no special ranking boost since 2021). Evaluate whether maintaining AMP is worth the overhead.

### 12. Audit Mobile Navigation UX
- Hamburger menus: ensure links are accessible to crawlers (don't hide nav in JS-only components)
- Sticky headers: ensure they don't consume too much viewport height
- Footer links: verify they're not too small or too dense on mobile
- Check that all primary navigation links are crawlable in mobile HTML source:
  ```bash
  curl -s https://domain.com/ | grep -i '<nav' -A 50 | grep href
  ```

---

## Common Issues and Fixes

| Issue | GSC Report | Fix |
|-------|-----------|-----|
| Missing viewport tag | "Viewport not configured" | Add `<meta name="viewport" content="width=device-width, initial-scale=1">` |
| Text too small | "Text too small to read" | Set body font ≥ 16px; use relative units |
| Tap targets too small/close | "Clickable elements too close" | Increase tap target size to 48x48px; add spacing |
| Intrusive interstitials | Mobile ranking signal | Delay pop-ups; reduce size; use banners not overlays |
| Horizontal scrolling | Layout broken | Add `overflow-x:hidden` on body; fix fixed-width elements |
| Mobile content different from desktop | Content parity issue | Ensure key content isn't hidden on mobile |
| Mobile images too large | Slow LCP on mobile | Use `srcset` with appropriately sized images per breakpoint |
| Fixed-width layout | Zoomed-out mobile rendering | Convert to responsive/fluid layout with CSS flexbox/grid |

---

## Tools to Use

| Tool | Purpose |
|------|---------|
| Google Search Console | Mobile Usability report, Core Web Vitals (mobile), URL Inspection |
| Google Mobile-Friendly Test | Quick per-page mobile check |
| Chrome DevTools Device Mode | Visual responsive testing at all breakpoints |
| PageSpeed Insights | Mobile-specific performance score and CWV |
| Screaming Frog | Crawl in Googlebot Smartphone mode (Configuration > User Agent) |
| BrowserStack | Real device testing across iOS/Android |
| WebPageTest | Mobile simulation with real device throttling |
| Lighthouse | Mobile-specific audit in Chrome DevTools |

---

## How to Measure Success

**Baseline metrics:**
- GSC Mobile Usability: count of pages with errors (by error type)
- PSI mobile score
- Mobile Core Web Vitals (LCP, INP, CLS) from GSC
- Mobile vs desktop organic traffic ratio (GSC Performance > Devices)

**30-day targets:**
- [ ] Zero "Viewport not configured" errors in GSC Mobile Usability
- [ ] Zero "Text too small to read" errors
- [ ] Zero "Clickable elements too close together" errors
- [ ] All key pages pass Google Mobile-Friendly Test
- [ ] No intrusive interstitials on page load for any key landing pages

**90-day targets:**
- [ ] GSC Mobile Usability shows 0 pages with errors (or acceptable baseline explained)
- [ ] Mobile Core Web Vitals: LCP < 2.5s, CLS < 0.1 for top pages
- [ ] Mobile organic traffic share ≥ industry benchmark (typically 55-65%)
- [ ] Mobile conversion rate gap vs desktop narrowed (if e-commerce tracking available)

**Reporting output:**
- Mobile Usability Audit (before/after error counts by type)
- GSC Mobile Usability screenshots
- PageSpeed Insights before/after comparison (mobile tab)
- Mobile vs desktop traffic analysis from GSC
