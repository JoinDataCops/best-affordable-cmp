# Best affordable CMP

Let's be real. The CMP market just had its biggest disruption since GDPR launched.

Cookiebot doubled SMB pricing in August 2025. Premium base went from around €15 to around €30 per month per domain. Premium Small got restricted to 4+ domains, forcing 1 to 3 domain accounts onto Premium Medium. That's effectively a 2x hike for the people who can least afford it. Trustpilot lit up with negative reviews for months.

Then the regulators stepped in. CNIL fined SHEIN €150M and Google €325M. The lesson: a CMP that only renders a banner without blocking scripts pre-consent is fine bait, not protection.

IAB TCF v2.3 became mandatory February 28 2026. Anything still on v2.2 today is non-compliant.

I tested every CMP that lists a public price under $50 per month. Plus the enterprise incumbents (OneTrust, Didomi, Sourcepoint) for context. Plus the self-hosted options (Klaro, CCM19) for the operators who'd rather own the stack.

Here's the honest read on what's actually affordable in 2026, what looks cheap and isn't, and where the free tiers are real vs where they're traps.

The thing nobody publishes: a price-per-1,000-pageviews table at 10K, 100K, and 1M traffic levels. That's the only comparison that means anything once you account for overage, subpage auto-upgrade, silent disable at cap, and white-label fees.

---

## Quick stuff people keep asking

**Is there a genuinely free CMP in 2026?** Yes, a few. CookieYes free covers 15K pageviews on 1 domain. CookieHub free covers 1K sessions per month (roughly 25K pageviews on a content site). Termly free covers 10K banner views with 1 policy. Microsoft Clarity is free without limits but it's analytics with a basic banner, not a real CMP. Klaro and CCM19 are self-hosted free if you can run your own infra.

**Is Cookiebot still affordable?** Not really, post-August 2025. Premium Small was restricted to 4+ domains. Single-domain operators got pushed to Premium Medium at €30 per month. CookieHub at €30 per month covers 120K sessions with TCF 2.3 white-label. Same money, way more headroom.

**What's the cheapest TCF 2.3 certified CMP?** CookieHub Business at €30 per month includes TCF 2.3 plus white-label plus 120K sessions to 1M sessions. Sirdata's free tier is TCF 2.3 in exchange for data sharing. Klaro self-hosted is free but requires you to handle vendor list updates manually.

**Do I need a paid CMP for a small site?** If you're under 15K pageviews per month and don't run programmatic ads, CookieYes free, Cookiebot free, or CookieHub free are all valid. Once you hit programmatic, TCF 2.3 is non-optional and the free tiers start showing limits.

**What about CookieYes vs Cookiebot for WordPress?** CookieYes for WordPress with 1M+ active installs. Free tier covers 15K pageviews. Cookiebot's WordPress plugin works but the August 2025 pricing reset moved it out of "affordable" territory for single-site operators.

---

## Genuinely affordable CMPs (under $30 per month)

This is the tier where most SMBs land. Real free tiers, real paid tiers under $30, real TCF 2.3 support where applicable.

**1. CookieYes**

The Good: Genuine free tier with 15K pageviews per month, basic banner, and one-domain auto-scan. Native WordPress plugin (formerly Cookie Law Info) with 1M+ active installs. Drop-in install for the long tail of small sites.

Frustrations: Per-domain pricing punishes multi-site operators. Agencies pay $10 per month Pro x N domains instead of one bundled fee. No DSAR automation, no API access, no policy generator on lower tiers. Growing businesses stitch in second tools fast.

Wish List: True multi-domain pricing (one account, many sites) instead of stacking per-domain subs.

Value for Money: **6.5/10.** Solid free CMP for one WordPress site. Anything more than one domain or DSAR-adjacent and the per-domain math gets ugly fast.

Pricing: Free (15K pageviews, 1 domain). Basic ~$10/mo. Pro $40/mo (300K pageviews). Ultimate $55/mo (unlimited pageviews). All per domain. Overage $0.30 per 1K pageviews.

---

**2. CookieHub**

The Good: Session-based pricing instead of pageview metering. A single visitor browsing 30 pages still counts as 1 session. Dramatically cheaper than Cookiebot for content-heavy sites. Genuinely useful free tier: 1,000 sessions per month (roughly 25K pageviews) with proof of consent and Google Consent Mode v2. Business tier at €30 includes TCF 2.3 and white-label.

Frustrations: Syncing settings across multiple domains is reported as cumbersome. G2 reviews note limited features compared to OneTrust/Usercentrics tier. No A/B testing or advanced consent analytics.

Wish List: Multi-domain settings sync that actually works at the click of a button.

Value for Money: **7.5/10.** The honest mid-market pick. Most of what you need from Cookiebot at roughly half the cost, especially after the 2025 Cookiebot price hike.

Pricing: Free (1K sessions). Starter €6/mo (5K sessions). Basic €10/mo (30K sessions). Business €30/mo (120K to 1M sessions, IAB TCF 2.3, white-label). Enterprise custom. Overage ~€0.10 per 1K.

---

**3. Termly**

The Good: Bundles legal policy generation (privacy policy, ToS, disclaimer) with the CMP. Useful one-stop for SMBs and freelancers. Aggressive entry pricing. Starter at $10 per month, Pro+ at $15 per month with 50K monthly banner views.

Frustrations: Free/Starter plan caps (1 to 2 policies, 10 edits, quarterly scans) push casual users to upgrade fast. Multi-platform users complain it's hard to justify cost when running multiple sites. Pricing scales awkwardly.

Wish List: Bundled / volume pricing for users running 3+ sites or platforms.

Value for Money: **7/10.** Best-value all-in-one privacy stack for solo operators and small SaaS. Falls apart if you need to scale past a couple of sites.

Pricing: Free (1 policy, 10K banner views). Starter $10/mo. Pro+ $15/mo (2 policies, 50K banner views).

---

**4. Iubenda**

The Good: Mature 360 degree privacy suite. Policy generator, CMP, T&C generator, DSAR, whistleblowing, accessibility, all under one team.blue umbrella since February 2022. Google Gold CMP Partner (December 2024). Full Consent Mode v2.

Frustrations: Trustpilot has documented complaints about post-cancellation "threatening emails" and being told account deletion was the only way to stop them. Customer support response times reportedly stretch a week or more on lower tiers. Some users report month-long waits with arrogant responses.

Wish List: Let paying customers download/export their custom policies they paid for.

Value for Money: **7/10.** Solid mid-market choice if you operate in many EU languages and don't need premium support. Not for shops that ever cancel and want their docs back.

Pricing: Free (basic, up to 3 services). Essentials $6.99/site/mo. Advanced $27.99/site/mo. Ultimate $119.99/site/mo (unlimited services, no branding).

---

**5. CookieFirst**

The Good: Google CMP Gold partner with native Consent Mode v2, GTM integration, and 44+ language auto-translated cookie policies. Cheapest serious CMP in the iubenda family.

Frustrations: Acquired by iubenda (team.blue) in January 2025. Typical post-acquisition concerns about roadmap independence and price drift. Free tier is limited to 1 third-party script. Most real sites need to start at paid immediately.

Wish List: Clear post-acquisition roadmap.

Value for Money: **6.5/10.** Solid no-nonsense CMP at agency-friendly pricing. Just keep an eye on what iubenda does with the brand long-term.

Pricing: Free (1 script). Basic €9/mo (€99/yr). Plus €19/mo (€209/yr). Enterprise custom. Soft 250K pageviews per domain on all plans.

---

**6. Borlabs Cookie**

The Good: WordPress-native plugin with deep integration. Facebook Pixel assistant, content blockers, IAB TCF support, geo-restriction. Library of 350+ pre-built cookie/script packages keeps maintenance low for typical WP stacks.

Frustrations: WordPress-only. Zero portability if you migrate to Shopify, Webflow, or a headless stack. Once your annual subscription lapses, premium features (library, geo, IAB TCF, scanner, translations) stop working.

Wish List: More resilient compatibility with popular caching/optimization plugins.

Value for Money: **7/10.** If you live on WordPress and don't plan to leave, hard to beat at the price. If you might re-platform, you'll be re-implementing consent.

Pricing: Personal €49/yr (1 site). Business €109/yr (5 sites). Agency Small €229/yr (25 sites). Agency Large €499/yr (99 sites). Annual only, excl. VAT.

---

**7. Sirdata**

The Good: Deeply embedded in the publisher market. 20,000+ publisher sites running ABconsent CMP. IAB TCF v2.1 certified and well-tuned for programmatic / AdTech use cases. Per-purpose vendor management, leak prevention.

Frustrations: The "free in exchange for your data" model is a non-starter for brands with strict first-party data policies. Less brand-recognized in North America than Didomi/OneTrust/Osano. Long sales cycles in the US.

Wish List: A genuinely paid/free-without-data-share entry tier for publishers who can't share visitor data.

Value for Money: **6.5/10.** Best-in-class for European publishers who can trade aggregate data for free CMP. Niche elsewhere.

Pricing: Free plan (data-share model). Paid ABconsent plans start at €25/mo with 14-day trial.

---

**8. Secure Privacy**

The Good: Coverage of 55+ global privacy laws including GDPR, CCPA/CPRA, LGPD, and India's DPDP Act. Broader than most SMB-tier CMPs. Aggressive entry pricing ($8.33 per month starting tier) plus a free plan with Google Consent Mode v2 already wired in.

Frustrations: Smaller brand than OneTrust/Didomi/Cookiebot. Enterprise procurement often requires extra security questionnaires. Advanced reporting and customization gated to higher tiers. Entry-tier users hit limits fast.

Wish List: Stronger SOC 2 / ISO badges and procurement collateral for enterprise buyers.

Value for Money: **7/10.** A solid budget CMP for SMBs that nails Consent Mode v2 out of the box. Not the pick if you want enterprise polish.

Pricing: Free plan. Paid plans start at $8.33/mo. Custom Enterprise plan available.

---

**9. ConsentManager**

The Good: Strong A/B testing + ML-driven banner optimization, with vendor claiming 15%+ avg consent rate lift. Live reporting with 12 dimensions and 30+ metrics. Deepest analytics in the mid-market CMP segment.

Frustrations: Starts at €19 to €23 per month. Pricier than CookieHub/CookieFirst at the same traffic tier. Bulk editing of new cookies and the auto-detected provider search are reported as buggy/unreliable.

Wish List: More reliable bulk cookie editing and provider auto-detection.

Value for Money: **7/10.** If consent rate is a real KPI and you'll actually use the A/B + analytics, worth the premium. Otherwise an iubenda or CookieHub does the job for less.

Pricing: From €19 to €23/mo (5 tiers + free trial).

---

## The mid-tier (under $200 per month)

Where things get interesting. Cookiebot lives here post-2025. So does Enzuzo, Usercentrics, and Osano.

**10. Cookiebot**

The Good: Established Usercentrics-owned CMP with broad regulator/agency familiarity. TCF v2.2 + Google CMP partner status. Free plan covers 1 domain up to 50 subpages. Mature scanner with reliable cookie/script auto-detection across complex sites.

Frustrations: August 2025 pricing reset. Premium base doubled from around €15 to around €30 per month per domain. Premium Small was restricted to 4+ domains, forcing 1 to 3 domain accounts onto Premium Medium. Effectively a 2x price hike. Customers report inadequate notification of price changes and poor communication. Multiple Trustpilot reports of large auto-debits before scan results, and bot scanners producing unrealistically high invoices.

Wish List: Honest, advance-notice price changes with grandfathering for existing accounts.

Value for Money: **5.5/10.** Once the default pick for European agencies. Post-2025 price reset, increasingly the option people are switching away from.

Pricing: Free (1 domain, 50 subpages). Premium Lite €7/mo. Premium Small €15/mo (4+ domains). Premium Medium €30/mo (3,500 subpages). Premium Large €50/mo. Premium XL €90/mo.

---

**11. Enzuzo**

The Good: Only CMP with a true Shopify-native integration that bundles policy generation, cookie consent, DSAR automation and multi-domain into the Shopify dashboard. Google Gold CMP Partner certification.

Frustrations: Free-tier privacy policy customization is limited. Bespoke text and language options gated to paid plans. Lower-tier users report slow support escalation. Some complain of no in-app way to contact the company.

Wish List: Smoother PLG-to-mid-market pricing curve (less cliff at $300).

Value for Money: **7.5/10.** For Shopify and SMB ecommerce, the strongest dedicated option. Fast, affordable, multi-domain. Outside Shopify, the value thins out.

Pricing: Free tier. Starter $9/mo ($7 annual). Growth $29/mo ($22 annual). PLG Pro $59/mo annual (10 domains). Mid-market starts $300/mo for high-traffic.

---

**12. Usercentrics**

The Good: Strong EU/GDPR pedigree (Munich-based). Plus Cookiebot product line for SMBs after the 2021 merger. Affordable entry tiers (Essential ~€7/mo, Free up to 1,000 sessions) compared to OneTrust/TrustArc enterprise pricing.

Frustrations: Auto-upgrade to higher tiers when session limits are exceeded. Surprise charges flagged repeatedly in reviews. Inaccurate session-limit warnings and known billing bugs cited by Capterra reviewers.

Wish List: Predictable pricing. Soft cap or warning instead of automatic tier upgrade.

Value for Money: **6.5/10.** Solid CMP for EU-first teams who can stomach the support and billing rough edges.

Pricing: Free under 1K sessions. Essential ~€7/mo. Plus ~€15/mo. Pro ~€30/mo (3 domains, 15K sessions). Business ~€50/mo (10 domains, 50K sessions).

---

**13. Osano**

The Good: Industry-only $500,000 "No Fines, No Penalties" contractual guarantee that covers regulatory fines if Osano is implemented per their guidance. Strong AI-assisted cookie classification with confidence scores users actually trust. Plus a free tier for very small sites.

Frustrations: Self-serve cookie consent now starts at $199 per month for a single domain capped at 30,000 visitors. Substantially more than peers like CookieYes/Termly. Banner customization is repeatedly called out as limited. Users want more layout flexibility and template options.

Wish List: Public, granular pricing for the privacy modules instead of mandatory sales calls.

Value for Money: **7/10.** Premium-priced CMP with a real fines guarantee. Worth it if compliance risk is your top fear. Hard to justify if you just need a banner.

Pricing: Free for very small sites. Plus starts at $199/mo for 1 domain / 30K monthly visitors.

---

## The enterprise tier (mostly not affordable)

For context only. If you're searching "best affordable CMP", these are not for you, but you should know what you're saving by skipping them.

**14. OneTrust**

The Good: Deepest module catalog in the category. Consent, DSAR, data mapping, vendor risk, PIA/DPIA, GRC, ESG. Single vendor for enterprise privacy. Dominant enterprise market share.

Frustrations: Massive layoffs. 950 (25%) in June 2022, additional rounds in July 2024 and June 2026. Pricing opaque. New minimum $10K per year as of Q2 2026. Mid-market deals run $40K to $120K, enterprise $120K to $500K+. Closed Planetly (carbon module) November 2022, laying off all 200 employees one year after acquisition.

Wish List: Published pricing or even just a starting floor.

Value for Money: **6/10.** If you're a Fortune 500 procurement team, OneTrust is the safe checkbox. Everyone else, you're paying enterprise tax for features you won't use.

Pricing: No public pricing. Minimum $10K/year (Q2 2026). Mid-market $40K to $120K/yr. Enterprise $120K to $500K+/yr.

---

**15. Didomi**

The Good: Two big 2025 acquisitions (Addingwell server-side tagging, April 2025; Sourcepoint CMP rival, May 2025) make Didomi the de facto European consolidator with CMP + sGTM under one roof. Backed by an $83M Marlin Equity majority stake.

Frustrations: Setup complexity is the recurring complaint. Per-partner triggers in GTM, technical-level integration, multi-day implementations. Dashboard called "unintuitive" and "clunky" once you're managing many policies/vendors.

Wish List: Cleaner unified dashboard.

Value for Money: **7.5/10.** If you're a European publisher or adtech-heavy site, the Didomi + Sourcepoint + Addingwell stack is enterprise-grade. For everyone else, the setup overhead is real.

Pricing: No public pricing. Indicative range €50/mo to $1,000+/mo. Annual contracts $2K to $15K depending on domains and traffic.

---

**16. Sourcepoint, Quantcast Choice, Ketch, TrustArc, Securiti, DataGrail, Privado, BigID, Transcend**

These are enterprise privacy-ops platforms. CMP is one module among many. None publish accessible pricing. Ketch has a free tier up to 5K users per month and Starter at $150 per month, which is the most affordable in this group. Quantcast Choice has been discontinued as of late 2025. The rest land $10K to $150K+ per year.

Skipping the full dossiers because they're not in the "affordable" conversation. The brief read: if you're not a Fortune 500 with a privacy ops team, these are not your tools.

---

## DataCops

DataCops isn't a like-for-like Cookiebot replacement. It's the trust-infrastructure layer underneath whichever CMP plus analytics plus CAPI stack you run. The CMP is one of the 5 products bundled, alongside first-party analytics, server-side CAPI, signup fraud detection, and fraud traffic validation.

The Good: TCF 2.2 certified first-party CMP (consent state stored on your subdomain, not a vendor's domain). Customizable banner design. Fraud-filtered consent signals (don't honor consent from bots). Plus CNAME-based first-party tracking, server-side CAPI to Meta, Google, TikTok, LinkedIn, IP database with 146.4B datacenter IPs, 202B residential, 11.9B VPN, signup fraud detection, all in the same stack. White-label CMP on Talk-to-Sales tier. Free plan includes the CMP at no cost forever.

Frustrations: SOC 2 Type II is in progress, not complete. Brand is newer than Cookiebot or OneTrust. TCF 2.3 upgrade path is on the roadmap, currently TCF 2.2 certified. Fewer enterprise integrations than category leaders.

Wish List: Faster SOC 2. TCF 2.3 certification ASAP given the Feb 2026 mandate.

Value for Money: **8/10.** The bundle math is the wedge. Free CMP plus 4 other products (analytics, CAPI, signup fraud, fraud filter) on a single CNAME-based stack. Most affordable CMPs are CMP-only.

Pricing: Free (2,000 sessions, 500 signup verifications, free CMP, unlimited bot detection). $7.99 Growth (5,000 sessions). $49 Business. $299 Organization. Enterprise talk-to-sales with white-label CMP.

---

## So what should you actually use?

There's no single answer. The right pick depends on your traffic, your stack, and your tolerance for setup work.

- Want a free CMP for a single WordPress site under 15K pageviews? CookieYes free or CookieHub free.

- Want TCF 2.3 certified CMP under €30 per month? CookieHub Business at €30.

- Running Shopify and need policy generation in the same tool? Enzuzo or Termly.

- Already paying Cookiebot and feeling the August 2025 hike? Migrate to CookieHub. Same money, way more sessions.

- Need consent + analytics + CAPI + fraud filter in one stack? DataCops. Free tier includes the CMP.

- Need WordPress-native and don't plan to ever leave WP? Borlabs Cookie.

- Need a $500K fines guarantee for compliance-heavy regulated industry? Osano. Premium price, real warranty.

- Need enterprise privacy ops with DSR automation, data mapping, vendor risk? Ketch (best published pricing) or DataGrail (strong AI tooling).

- You're a publisher with TCF programmatic adtech needs in the EU? Sirdata or Sourcepoint (mid-merger).

- You can run your own infra? Klaro or CCM19 self-hosted.

---

## The mistake I see people make

They pick the cheapest CMP without checking pre-consent script blocking, TCF 2.3 readiness, audit log, and the dark-pattern-free defaults. Then a regulator audit hits and the fact that they had a banner doesn't matter. The CNIL fines on SHEIN (€150M) and Google (€325M) are public reminders. A CMP that renders a banner without enforcing the consent state at the script level is fine bait, not protection.

---

## Now your turn

What's your CMP costing you in 2026? And does it actually block scripts pre-consent or just render a banner? Drop your stack, I'm curious how others are navigating the post-Cookiebot-hike landscape.

---

Research by [DataCops](https://www.joindatacops.com) — first-party tracking, consent infrastructure, fraud prevention, and server-side CAPI for Meta, Google, TikTok, and LinkedIn.
