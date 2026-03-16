# HTTPS — Technical SEO Playbook

## When to Use This

Use this playbook when:
- A client site is still serving on HTTP (not HTTPS)
- Mixed content warnings are showing in browser console
- SSL certificate is expired or about to expire
- A site migration moved from HTTP to HTTPS and something went wrong
- GSC shows HTTPS coverage issues or traffic dropped after migration to HTTPS
- The site serves both HTTP and HTTPS versions simultaneously
- HSTS is not configured and needs to be implemented
- A sub-domain or page is not covered by the SSL certificate
- After a CDN (Cloudflare) setup that may have introduced SSL configuration issues

---

## Why HTTPS Matters for SEO

- Google confirmed HTTPS as a ranking signal in 2014 — still active
- Google Chrome labels HTTP sites as "Not Secure" — destroys user trust and CTR
- HTTP/2 (and HTTP/3) require HTTPS — significant performance benefits lost without it
- HTTPS protects referral data: `https://source.com → http://destination.com` strips referral to "direct" traffic
- Required for many browser features: Service Workers, geolocation, push notifications

---

## Step-by-Step Checklist

### 1. Verify SSL Certificate is Valid and Properly Configured
```bash
# Check certificate validity
echo | openssl s_client -connect domain.com:443 -servername domain.com 2>/dev/null | openssl x509 -noout -dates -subject -issuer

# Check for certificate errors
curl -vI https://domain.com 2>&1 | grep -E "subject:|issuer:|expire|SSL|TLS|certificate"

# Online check
# https://www.ssllabs.com/ssltest/analyze.html?d=domain.com
```

Target: SSL Labs grade of A or A+

### 2. Check Certificate Coverage (All Subdomains)
Verify the certificate covers:
- `domain.com` (apex/root domain)
- `www.domain.com`
- Any other subdomains used: `shop.domain.com`, `blog.domain.com`, etc.

Wildcard certificate covers `*.domain.com` but NOT `domain.com` (apex) — both must be included.

```bash
# Check SANs (Subject Alternative Names) — all covered domains
echo | openssl s_client -connect domain.com:443 -servername domain.com 2>/dev/null | openssl x509 -noout -text | grep -A1 "Subject Alternative Name"
```

### 3. Implement 301 Redirects from HTTP to HTTPS

**nginx:**
```nginx
# Redirect all HTTP to HTTPS
server {
    listen 80;
    listen [::]:80;
    server_name domain.com www.domain.com;
    return 301 https://$host$request_uri;
}
```

**Apache (.htaccess):**
```apache
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
```

**WordPress (wp-config.php):**
```php
define('FORCE_SSL_ADMIN', true);
if (strpos($_SERVER['HTTP_X_FORWARDED_PROTO'], 'http') !== false) {
    $_SERVER['HTTPS'] = 'on';
}
```

Verify the redirect is in place:
```bash
curl -I http://domain.com
# Should return: HTTP/1.1 301 Moved Permanently
# Location: https://domain.com/
```

### 4. Redirect WWW to Non-WWW (or Vice Versa) Consistently
Pick one canonical domain and 301 redirect the other. Never serve both.

```nginx
# Preferred: https://domain.com (non-www)
server {
    listen 443 ssl;
    server_name www.domain.com;
    return 301 https://domain.com$request_uri;
}

server {
    listen 443 ssl;
    server_name domain.com;
    # Main server configuration
}
```

### 5. Audit and Fix All Mixed Content
Mixed content = HTTPS page loading HTTP resources. Browsers block these or show warnings.

**Find mixed content:**
```bash
# Crawl with Screaming Frog > Reports > Mixed Content
# Or use Chrome DevTools > Console — look for:
# "Mixed Content: The page at 'https://...' was loaded over HTTPS, but requested an insecure resource 'http://...'"
```

**Fix in WordPress:**
- Use "Better Search Replace" plugin to update all `http://domain.com` to `https://domain.com` in database
- Or use WP CLI:
  ```bash
  wp search-replace 'http://domain.com' 'https://domain.com' --all-tables
  ```

**Fix in HTML/templates:**
```html
<!-- WRONG -->
<img src="http://domain.com/image.jpg">
<script src="http://cdn.example.com/library.js"></script>
<link rel="stylesheet" href="http://fonts.googleapis.com/css?family=Roboto">

<!-- CORRECT — use protocol-relative or https:// -->
<img src="https://domain.com/image.jpg">
<script src="https://cdn.example.com/library.js"></script>
<link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Roboto">
```

**Emergency fix — Content Security Policy upgrade-insecure-requests:**
```html
<!-- Add to <head> as temporary fix while cleaning up mixed content -->
<meta http-equiv="Content-Security-Policy" content="upgrade-insecure-requests">
```
This auto-upgrades HTTP requests to HTTPS in supporting browsers. Not a permanent fix — clean up mixed content properly.

### 6. Implement HSTS (HTTP Strict Transport Security)
HSTS tells browsers to ONLY use HTTPS for this domain, preventing HTTP downgrade attacks.

```nginx
# nginx — add to HTTPS server block
add_header Strict-Transport-Security "max-age=31536000; includeSubDomains; preload" always;
```

```apache
# Apache
Header always set Strict-Transport-Security "max-age=31536000; includeSubDomains; preload"
```

**HSTS stages (implement in order):**
1. Start with short max-age: `max-age=300` (5 minutes) — test that nothing breaks
2. Increase to `max-age=86400` (1 day) — verify
3. Increase to `max-age=31536000` (1 year) with `includeSubDomains`
4. Submit to HSTS preload list: `https://hstspreload.org/` (optional but recommended)

**Warning:** Once HSTS is enabled with `preload` and submitted, it's extremely difficult to revert. Only do this when you're confident the entire domain will always be HTTPS.

### 7. Update All Internal Links to HTTPS
Scraped HTTP internal links waste the redirect budget and slow page load.

```bash
# Find HTTP internal links with Screaming Frog
# Reports > Links > Filter by "http://" in href
```

In WordPress database:
```bash
# Find all remaining HTTP references
wp search-replace --dry-run 'http://domain.com' 'https://domain.com' --all-tables
# Remove --dry-run when confirmed
wp search-replace 'http://domain.com' 'https://domain.com' --all-tables
```

Update hardcoded URLs in code/config files:
```bash
grep -r "http://domain.com" /var/www/html/ --include="*.php" --include="*.js" --include="*.css"
```

### 8. Update Google Search Console and Analytics Properties
- Add HTTPS property in GSC (it's treated as a separate property from HTTP)
- Preferred: Use Domain property in GSC (covers all protocols/subdomains)
  - GSC > Add Property > Domain > `domain.com`
- Update Google Analytics to prefer HTTPS URLs
- Update canonical tags to use HTTPS URLs

### 9. Verify Sitemap Uses HTTPS URLs Only
```bash
curl -s https://domain.com/sitemap.xml | grep "<loc>" | head -20
# All should start with https://
```

If sitemap contains `http://` URLs, regenerate or find/replace:
```bash
curl -s https://domain.com/sitemap.xml | sed 's|http://|https://|g' > sitemap-fixed.xml
```

### 10. Check for SSL Certificate Auto-Renewal
Let's Encrypt certificates expire every 90 days — must be auto-renewed.

```bash
# Check certbot renewal status
certbot certificates
sudo systemctl status certbot.timer

# Test renewal without actually renewing
certbot renew --dry-run

# Check cron jobs for renewal
crontab -l | grep certbot
```

Cloudflare-managed SSL: auto-renews automatically — verify in Cloudflare dashboard > SSL/TLS.

### 11. Validate TLS Version (Security + Performance)
Old TLS 1.0 and 1.1 are deprecated. Must use TLS 1.2 minimum; TLS 1.3 recommended.

```bash
# Check TLS versions supported
nmap --script ssl-enum-ciphers -p 443 domain.com

# Or check with SSL Labs (easier)
# https://www.ssllabs.com/ssltest/
```

```nginx
# nginx — enforce TLS 1.2+
ssl_protocols TLSv1.2 TLSv1.3;
ssl_ciphers ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384;
ssl_prefer_server_ciphers off;
```

### 12. Monitor Certificate Expiry and HTTPS Health
```bash
# Check days until certificate expiry
echo | openssl s_client -connect domain.com:443 -servername domain.com 2>/dev/null | \
  openssl x509 -noout -enddate | \
  awk -F= '{print $2}' | \
  xargs -I{} date -d {} +%s | \
  awk -v now=$(date +%s) '{print int(($1-now)/86400) " days until expiry"}'
```

Set up alerts:
- Cloudflare: SSL/TLS > Edge Certificates — shows expiry date
- UptimeRobot or StatusCake: HTTPS monitoring with SSL expiry alerts
- Google Search Console: will alert on HTTPS errors in Coverage

---

## Post-Migration HTTPS Checklist

If migrating from HTTP to HTTPS:
- [ ] SSL certificate installed and valid
- [ ] 301 redirects HTTP → HTTPS for ALL URLs (not just homepage)
- [ ] www → non-www (or vice versa) redirect consistent
- [ ] All internal links updated to HTTPS
- [ ] All assets (images, CSS, JS) loading over HTTPS (no mixed content)
- [ ] Canonical tags updated to HTTPS
- [ ] XML sitemap updated to HTTPS URLs
- [ ] robots.txt sitemap directive updated to HTTPS
- [ ] HSTS header added (start with short max-age)
- [ ] Google Search Console: new HTTPS property added, sitemap submitted
- [ ] Google Analytics: default URL updated to HTTPS

---

## Common Issues and Fixes

| Issue | Symptom | Fix |
|-------|---------|-----|
| Mixed content warnings | Browser shows "Not Secure" despite HTTPS | Find and replace all HTTP asset URLs |
| SSL certificate expired | Browser warning page | Renew certificate; enable auto-renewal |
| HTTP not redirecting to HTTPS | Both versions accessible | Add 301 redirect in server config |
| Certificate doesn't cover www | Error on `www.domain.com` | Issue wildcard or multi-domain cert |
| Redirect loop | Infinite redirect | Check for conflicting redirect rules in CDN + server |
| Old HTTP links in database | Mixed content, wasted redirects | Database search-replace http:// to https:// |
| HSTS too aggressive too soon | Hard to undo if SSL breaks | Implement HSTS gradually with short max-age first |
| TLS 1.0/1.1 still enabled | SSL Labs grade C or below | Update ssl_protocols in server config |

---

## Tools to Use

| Tool | Purpose |
|------|---------|
| SSL Labs | Comprehensive SSL/TLS grade and vulnerability scan |
| Google Search Console | HTTPS property, Coverage errors |
| Screaming Frog | Mixed content detection, HTTP link audit |
| Chrome DevTools | Console mixed content warnings, Security panel |
| curl | Manual HTTP/HTTPS response code checking |
| certbot | Let's Encrypt certificate management |
| UptimeRobot / StatusCake | SSL expiry monitoring |
| HSTS Preload List | Submit domain for browser preloading |

---

## How to Measure Success

**Baseline metrics:**
- SSL Labs grade
- Count of HTTP pages still accessible (Screaming Frog crawl)
- Count of mixed content warnings (Screaming Frog + DevTools)
- Certificate expiry date

**30-day targets:**
- [ ] SSL Labs grade A or A+
- [ ] Zero mixed content warnings on all key pages
- [ ] 100% of HTTP URLs 301 redirecting to HTTPS equivalent
- [ ] HSTS header implemented (at least `max-age=86400`)
- [ ] Certificate auto-renewal confirmed active

**90-day targets:**
- [ ] HSTS max-age at 31536000 (1 year) with `includeSubDomains`
- [ ] All internal links using HTTPS (no wasted redirects)
- [ ] GSC shows HTTPS as canonical for all pages
- [ ] No SSL-related errors in GSC Coverage
- [ ] Consider HSTS preload list submission

**Reporting output:**
- SSL Labs full report screenshot (grade + certificate details)
- Mixed content audit (pages affected, resources fixed)
- Redirect audit (HTTP → HTTPS chain verification)
- GSC Coverage before/after HTTPS migration (if applicable)
