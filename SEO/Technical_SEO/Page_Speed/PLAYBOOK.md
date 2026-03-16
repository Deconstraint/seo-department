# Page Speed — Technical SEO Playbook

## When to Use This

Use this playbook when:
- A client's Core Web Vitals are in "Poor" or "Needs Improvement" status in GSC
- PageSpeed Insights score is below 50 on mobile
- Organic rankings have dropped without obvious content cause (speed may be a ranking factor)
- A site migration or redesign has degraded performance
- A new client audit reveals slow load times
- E-commerce client with high bounce rates and low conversion (speed directly impacts revenue)
- Google Search Console shows "Page Experience" signals trending negative
- A client wants to compete in a niche where competitors have fast sites

---

## Core Web Vitals Reference

| Metric | What It Measures | Good | Needs Improvement | Poor |
|--------|-----------------|------|-------------------|------|
| **LCP** (Largest Contentful Paint) | Loading performance | ≤ 2.5s | 2.5s–4s | > 4s |
| **INP** (Interaction to Next Paint) | Interactivity responsiveness | ≤ 200ms | 200–500ms | > 500ms |
| **CLS** (Cumulative Layout Shift) | Visual stability | ≤ 0.1 | 0.1–0.25 | > 0.25 |

---

## Step-by-Step Checklist

### 1. Establish Baseline Metrics
Before any changes, document:
- PageSpeed Insights score (mobile + desktop): `https://pagespeed.web.dev/`
- Core Web Vitals from GSC: Performance > Core Web Vitals
- Screaming Frog: `Configuration > Spider > Speed` — crawl all pages, note response times
- Real-user data (CrUX) vs lab data (Lighthouse) — CrUX is what Google uses for ranking

```bash
# Get Lighthouse score via CLI
npx lighthouse https://domain.com --output=json --output-path=./lighthouse-report.json --chrome-flags="--headless"
```

### 2. Fix LCP (Largest Contentful Paint)

**Identify the LCP element:**
- Open DevTools > Performance panel > Record page load > find LCP element
- Usually: hero image, H1 text, or above-fold background image

**Optimize images:**
```html
<!-- Preload LCP image immediately -->
<link rel="preload" as="image" href="/hero-image.webp" fetchpriority="high">

<!-- Use modern formats -->
<picture>
  <source srcset="/hero.avif" type="image/avif">
  <source srcset="/hero.webp" type="image/webp">
  <img src="/hero.jpg" alt="Hero" width="1200" height="600" loading="eager" fetchpriority="high">
</picture>
```

**Eliminate render-blocking resources:**
- Defer non-critical CSS: `<link rel="stylesheet" href="non-critical.css" media="print" onload="this.media='all'">`
- Defer non-critical JS: `<script src="analytics.js" defer></script>` or `async`

**Use CDN for static assets:**
- Cloudflare, CloudFront, or Fastly for CSS/JS/images
- Reduces TTFB (Time to First Byte) dramatically

### 3. Fix CLS (Cumulative Layout Shift)

**Root causes and fixes:**

Images without dimensions (most common):
```html
<!-- WRONG — no dimensions, causes layout shift when image loads -->
<img src="image.jpg" alt="Product">

<!-- CORRECT — explicit dimensions prevent layout shift -->
<img src="image.jpg" alt="Product" width="800" height="600">
```

Dynamic content injection above existing content:
```css
/* Reserve space for ads/banners before they load */
.ad-container {
  min-height: 250px;
  min-width: 300px;
}
```

Font swap causing text reflow:
```css
/* Use font-display: optional to prevent layout shift */
@font-face {
  font-family: 'MyFont';
  src: url('/fonts/myfont.woff2') format('woff2');
  font-display: optional; /* or 'swap' with adequate space reserved */
}
```

Preload critical fonts:
```html
<link rel="preload" href="/fonts/myfont.woff2" as="font" type="font/woff2" crossorigin>
```

### 4. Fix INP (Interaction to Next Paint)

**Identify slow interactions:**
- Chrome DevTools > Performance Insights > Interactions
- Look for: click handlers, form submissions, menu opens taking > 200ms

**Main thread optimization:**
```javascript
// WRONG — heavy synchronous computation blocks the thread
button.addEventListener('click', () => {
  const result = heavyComputation(); // blocks for 500ms
  updateUI(result);
});

// CORRECT — break up long tasks
button.addEventListener('click', () => {
  setTimeout(() => {
    const result = heavyComputation();
    updateUI(result);
  }, 0);
});

// BETTER — use scheduler API
button.addEventListener('click', async () => {
  await scheduler.yield(); // yield to browser for input processing
  const result = heavyComputation();
  updateUI(result);
});
```

**Reduce JavaScript bundle size:**
- Code split with dynamic imports: `const module = await import('./heavy-module.js')`
- Remove unused JS: Lighthouse > Coverage tab in DevTools
- Lazy load below-fold components

### 5. Optimize Images Sitewide
```bash
# Batch convert to WebP using CLI
for img in *.jpg *.png; do
  cwebp -q 80 "$img" -o "${img%.*}.webp"
done

# Check image optimization opportunities
npx squoosh-cli --webp '{"quality":80}' *.jpg
```

Settings to enforce:
- Serve WebP/AVIF formats with `<picture>` element fallbacks
- Compress JPEGs to 80% quality (imperceptible quality loss, 60-70% file size reduction)
- Lazy-load below-fold images: `<img loading="lazy">`
- Never lazy-load above-fold (LCP) images — use `loading="eager"`
- Use correct srcset for responsive images:
  ```html
  <img srcset="image-400.webp 400w, image-800.webp 800w, image-1200.webp 1200w"
       sizes="(max-width: 600px) 400px, (max-width: 1000px) 800px, 1200px"
       src="image-1200.webp" alt="Product">
  ```

### 6. Implement Effective Caching
```nginx
# nginx — aggressive caching for static assets
location ~* \.(jpg|jpeg|png|gif|ico|css|js|webp|avif|woff2)$ {
  expires 1y;
  add_header Cache-Control "public, immutable";
}

# HTML — short cache, stale-while-revalidate
location ~* \.html$ {
  expires 1h;
  add_header Cache-Control "public, stale-while-revalidate=86400";
}
```

For WordPress: Use WP Rocket, LiteSpeed Cache, or W3 Total Cache.

### 7. Reduce Time to First Byte (TTFB)
Target: TTFB < 800ms (Google's threshold)
```bash
# Measure TTFB
curl -o /dev/null -s -w "TTFB: %{time_starttransfer}s\n" https://domain.com
```

Fixes:
- Upgrade hosting (shared hosting often has 2-5s TTFB; VPS/dedicated < 200ms)
- Enable server-side caching (Redis, Varnish, full-page cache)
- Reduce database query time (WordPress: use query monitor plugin to find slow queries)
- Use a CDN (Cloudflare's proxy reduces TTFB by serving from edge nodes)
- Enable HTTP/2 or HTTP/3 on the server

### 8. Minify and Compress Text Resources
```nginx
# nginx — enable gzip compression
gzip on;
gzip_types text/plain text/css application/javascript application/json image/svg+xml;
gzip_min_length 256;
gzip_comp_level 6;

# Better: use Brotli compression (20-30% better than gzip)
brotli on;
brotli_types text/plain text/css application/javascript application/json;
```

CSS/JS minification:
- Build-level: webpack, Vite, Parcel handle this automatically
- WordPress: WP Rocket > Minify CSS/JS, or Autoptimize plugin

### 9. Eliminate Render-Blocking Resources
Identify render-blocking resources in Lighthouse audit.

Prioritization approach:
```html
<!-- Critical CSS: inline it directly in <head> -->
<style>
  /* Only above-fold, critical styles */
  body { font-family: sans-serif; margin: 0; }
  .hero { background: #000; min-height: 60vh; }
</style>

<!-- Non-critical CSS: load async -->
<link rel="preload" href="/css/main.css" as="style" onload="this.rel='stylesheet'">
<noscript><link rel="stylesheet" href="/css/main.css"></noscript>

<!-- Defer all non-critical JS -->
<script src="/js/app.js" defer></script>

<!-- Preconnect to critical third parties -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
```

### 10. Audit Third-Party Scripts
Third-party scripts (chat widgets, analytics, ad networks, heatmaps) are often the #1 cause of slow INP and LCP.

Audit:
```javascript
// In DevTools Console — see all third-party requests
performance.getEntriesByType('resource')
  .filter(r => !r.name.includes('domain.com'))
  .sort((a, b) => b.duration - a.duration)
  .slice(0, 10)
  .forEach(r => console.log(r.name, Math.round(r.duration) + 'ms'));
```

Fix: Load non-critical third-party scripts with `async` or `defer`, or use a facade (e.g., YouTube facade for embedded videos):
```html
<!-- YouTube Facade — only loads YouTube JS on click -->
<lite-youtube videoid="VIDEO_ID"></lite-youtube>
<!-- npm: lite-youtube-embed -->
```

### 11. Enable HTTP/2 Push or Resource Hints
```html
<!-- Preconnect to reduce DNS/TCP time for critical origins -->
<link rel="preconnect" href="https://fonts.googleapis.com">

<!-- Prefetch resources needed for next page navigation -->
<link rel="prefetch" href="/next-page.html">

<!-- DNS prefetch for third-party domains -->
<link rel="dns-prefetch" href="https://www.google-analytics.com">
```

### 12. Measure Impact and Iterate
After implementing fixes:
```bash
# Re-run Lighthouse
npx lighthouse https://domain.com --output=html --output-path=./after-report.html

# Compare CrUX data (28-day rolling average — changes take time to appear)
# GSC > Core Web Vitals > check if "Poor URLs" count is decreasing
```
- Field data (CrUX in GSC) lags behind your fixes by ~28 days
- Lab data (PageSpeed Insights) shows improvements immediately
- Track both; report both to clients

---

## Common Issues and Fixes

| Issue | Symptom | Fix |
|-------|---------|-----|
| Unoptimized hero image | High LCP | Convert to WebP, add `fetchpriority="high"`, preload tag |
| Images without width/height | High CLS | Add explicit dimensions to all `<img>` tags |
| Render-blocking CSS/JS | Slow FCP + LCP | Defer/async non-critical scripts; inline critical CSS |
| No server caching | High TTFB | Enable Redis/Varnish; use CDN |
| Font loading causes layout shift | CLS from text reflow | Use `font-display: optional` or preload fonts |
| Heavy third-party scripts | Slow INP | Defer, async, or remove non-essential scripts |
| No image compression | Slow LCP | Run through ImageOptim/Squoosh, serve WebP |
| No CDN | High TTFB globally | Implement Cloudflare or CloudFront |
| Shared hosting | Consistently high TTFB | Migrate to VPS or managed hosting |

---

## Tools to Use

| Tool | Purpose |
|------|---------|
| PageSpeed Insights | Lab + field data (CrUX) for any URL |
| Google Search Console | Core Web Vitals report (real user data) |
| Lighthouse (DevTools/CLI) | Full performance audit with recommendations |
| Chrome DevTools > Performance | Profiling, LCP element identification, INP analysis |
| WebPageTest | Filmstrip view, waterfall chart, global testing |
| GTmetrix | Alternative performance scoring + waterfall |
| Screaming Frog | Crawl response time across all pages |
| ImageOptim / Squoosh | Image compression |
| Bundlephobia | Check JavaScript package size before adding |

---

## How to Measure Success

**Baseline metrics (capture before any changes):**
- PSI mobile score
- LCP (ms), INP (ms), CLS (score)
- TTFB (ms) — `curl` measurement
- GSC CWV: Poor URLs count, Needs Improvement count
- Page weight (total KB) from WebPageTest

**30-day targets:**
- [ ] PSI mobile score ≥ 50 (from < 50 baseline)
- [ ] LCP < 4s (from > 4s baseline)
- [ ] CLS < 0.25 (from > 0.25 baseline)
- [ ] All `<img>` tags have explicit width and height attributes
- [ ] Hero image served in WebP with preload tag

**90-day targets:**
- [ ] LCP < 2.5s ("Good" threshold) for priority pages
- [ ] INP < 200ms for all interactive pages
- [ ] CLS < 0.1 ("Good" threshold)
- [ ] GSC CWV "Poor URLs" count reduced by ≥50%
- [ ] PSI mobile score ≥ 75 for key landing pages

**Reporting output:**
- PageSpeed Insights screenshots before/after (mobile)
- GSC Core Web Vitals trend graph
- CWV improvement table (LCP/INP/CLS baseline vs current per key page)
