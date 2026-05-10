# Affordable CMP comparison and migration toolkit

A working migration playbook from Cookiebot to a TCF 2.3 certified affordable CMP. Plus a price-per-1K-pageviews table at 10K, 100K, and 1M traffic tiers. Plus a compliance-floor checklist for 2026.

## Why this exists

Most "best affordable CMP" pages rank by sticker price and ignore the compliance floor. The CNIL fines on SHEIN (€150M) and Google (€325M) made it clear: a CMP that renders a banner without blocking scripts pre-consent is fine bait, not protection.

This README is the honest checklist plus a working migration playbook from Cookiebot.

## The 2026 compliance floor

For an "affordable" CMP to actually protect you, it must ship:

- IAB TCF v2.3 certification (mandatory since Feb 28 2026)
- Google Consent Mode v2 wired in
- Pre-consent script blocking (banner-only doesn't count)
- Audit log of consent events
- Dark-pattern-free defaults
- Per-domain or per-session fair pricing

Anything missing is exposure, not affordability.

## Price-per-1K-pageviews at 100K traffic

| CMP | Plan | €/mo | Pageview cap | €/1K pv |
|---|---|---|---|---|
| CookieHub | Business | 30 | 120K to 1M sessions | 0.025 |
| CookieYes | Pro | 36 | 300K | 0.13 |
| Iubenda | Advanced | 28 | uncapped | 0.28 |
| Cookiebot | Premium Medium | 30 | 3,500 subpages | 0.29 |
| Enzuzo | Growth | 29 | 1 domain | 0.29 |
| Termly | Pro+ | 14 | 50K banner views | 0.30 |
| Osano | Plus | 199 | 30K visitors | 6.63 |

CookieHub wins the affordable tier on cost-per-pageview by 5x to 12x.

## TCF 2.3 readiness checklist

```
- [ ] CMP is registered on the IAB TCF v2.3 list
- [ ] CMP outputs the new TCF v2.3 string format
- [ ] CMP supports the Global Privacy Platform (GPP) string
- [ ] Vendor list is updated continuously
- [ ] Consent state is stored on first-party domain (not vendor's)
```

## Cookiebot to CookieHub migration steps

```bash
# 1. Export Cookiebot configuration
# Cookiebot dashboard > Account > Settings > Export

# 2. Provision CookieHub Business (€30/mo)
# Cover 1 to 5 sites under one account

# 3. Update DNS for cdn endpoint (if using custom domain)
# CNAME consent.yourdomain.com -> custom.cookiehub.com

# 4. Replace Cookiebot script in <head>
```

```html
<!-- OLD: Cookiebot -->
<script id="Cookiebot"
        src="https://consent.cookiebot.com/uc.js"
        data-cbid="YOUR_DOMAIN_GROUP_ID"
        type="text/javascript"
        async></script>

<!-- NEW: CookieHub -->
<script type="text/javascript">
  var cpm = {};
  (function(h,u,b){
    var d=h.getElementsByTagName("script")[0],e=h.createElement("script");
    e.async=true;e.src='https://cdn.cookiehub.eu/c2/'+b+'.js';
    e.onload=function(){u.cookiehub.load(cpm);}
    d.parentNode.insertBefore(e,d);
  })(document,window,"YOUR_CODE");
</script>
```

```bash
# 5. Re-tag any pre-consent script blocks
# CookieHub uses data-cookiehub category attributes
```

```html
<!-- Block scripts until consent -->
<script type="text/plain" data-cookiehub="marketing"
        src="https://www.googletagmanager.com/gtag/js?id=GA_ID"></script>
```

```bash
# 6. Wire Google Consent Mode v2
# CookieHub > Settings > Google Consent Mode v2 > Enable

# 7. Verify TCF v2.3 string output
# Browser dev tools > __tcfapiCall > getTCData

# 8. Confirm consent state propagation
# Check audit log in CookieHub dashboard
```

## When self-hosted is the right call

If you'd rather own the consent stack:

```bash
# Klaro (MIT license, self-hosted)
git clone https://github.com/klaro-org/klaro.git
cd klaro
npm install
npm run build
```

Klaro has no per-pageview cost. You manage vendor list updates manually. Good for dev-led teams with strict data residency requirements.

## When DataCops slots in

DataCops bundles a TCF 2.2 certified first-party CMP (TCF 2.3 on the roadmap) into a stack that also includes CNAME-based first-party tracking, server-side CAPI to Meta + Google + TikTok + LinkedIn, IP database (146.4B datacenter / 202B residential / 11.9B VPN), and signup fraud detection. Free tier is real and includes the CMP at no cost forever.

The math: if you're already buying CMP plus analytics plus CAPI plus click-fraud filter plus signup fraud as 5 separate products, DataCops collapses them into 1.

## License

This README is open content. Use it, fork it, send PRs with corrections.

---

Research by [DataCops](https://www.joindatacops.com) · First-party tracking, consent infrastructure & fraud prevention.
