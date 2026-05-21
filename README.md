# Best affordable CMP

**"Affordable CMP" is the most misleading two-word search in privacy software.** Every result hands you a tool with a low headline price and calls it a day. None of them normalize the cost. None of them tell you that a $9/month CMP can quietly become more expensive than a $99/month one once your traffic grows, because the cheap one bills per pageview and the pricier one does not.

I went through the consent management market priced by what you actually pay at 10k, 100k, and 1M monthly pageviews, not by the number on the marketing page. The ranking below is sorted by real cost-to-value, with the hidden fees dragged into the light.

Here is the blunt part nobody selling a CMP will tell you. **A cheap CMP and an expensive CMP fail at the exact same place.** They are both a third-party script that 30 to 40% of privacy-conscious EU users block before it ever renders. You can pick the most affordable banner on this list and still have no consent record, and no fallback, for a third of your visitors.

This is not just a "which banner is cheapest" post. It is a post about what a CMP can and cannot do, and where the consent layer stops being your data problem. The architectural answer to the part a CMP cannot reach is first-party collection with two separated data tiers, which is what [DataCops](/first-party-consent-manager-platform) is built around. I will be specific about where that matters and, just as importantly, where it does not. Several tools below are simply good-value CMPs, full stop. See also [best CMP 2026](/resources/best-cmp-2026).

## Quick stuff people keep asking

**What is the cheapest consent management platform?** Free tiers exist, and several are genuinely free: CookieHub up to 1,000 sessions a month, ConsentManager up to 3,000 views, InMobi CMP (the old Quantcast Choice) free outright. The cheapest paid entry points sit around $5 to $9 a month. But "cheapest" depends entirely on your pageview volume, because per-pageview billing changes the ranking completely at scale.

**Is there a free CMP?** Yes, several. CookieHub, ConsentManager, and Enzuzo all have free versions. InMobi CMP is fully free. Sirdata is free for publishers who join its data partnership. Just read what the free tier excludes, because the feature you need is often the one behind the paywall.

**How much does a CMP cost per month?** Anywhere from free to $200-plus per domain for SMB and mid-market tools, and $10,000 to $175,000 per year for enterprise platforms. The honest budget answer for a small or mid-size site is $5 to $60 a month, as long as you watch the pageview tiers.

**Is CookieYes free?** [CookieYes](/alternative/cookieyes-alternative) has a free tier, yes. It is not in this batch's deep comparison, but the same rule applies: check the pageview cap and which features the free plan locks out.

**What is the cheapest GDPR-compliant CMP?** For WordPress sites, Borlabs Cookie at roughly €39/year for a single site is hard to beat, and it is first-party hosted. For non-WordPress sites, CookieHub or Enzuzo on their entry tiers are the cheapest credible options.

**Can I build my own consent management platform?** Technically yes, and a basic banner is not hard. But you would be rebuilding TCF string handling, Google Consent Mode v2 signaling, cookie scanning, and consent logging, then maintaining all of it as regulations change. For almost everyone, a $9/month CMP is cheaper than the engineering time.

**Do affordable CMPs work with Google Consent Mode v2?** The good ones do. Borlabs, CookieFirst, CookieHub, ConsentManager, and Enzuzo all support Consent Mode v2. Support and correct configuration are two different things, though. Secure Privacy's own 2026 data found 67% of Consent Mode v2 setups are non-compliant. The tool supporting it does not mean yours is wired right.

**What's the difference between a free and paid CMP?** Usually pageview or session caps, domain count, TCF support, DSR automation, audit logging, and support response time. The free tier is often a working trial, not a production plan. Map the limits to your real traffic before you commit.

## The gap every CMP on this list shares

Before the rankings, the structural thing. A CMP's job is consent: show a banner, capture a choice, gate scripts, log it. The good ones do that well. But there are five layers to the data problem, and a CMP only touches a couple of them, and not always cleanly.

Layer 1: [cookieless](/resources/best-cookieless-analytics) analytics is a European legal hack, not a global data solution. A CMP does not even play here. It manages consent for whatever analytics you run; it does not advise on collecting lawful data without cookies.

Layer 2: "Reject All" does not mean "no data." Anonymous session analytics are legal whether the user accepted or rejected. A CMP fires the rejection signal correctly and then assumes the session is dead. It is not. The anonymous, non-identifying part of that session was always legal to keep. Almost no CMP routes or preserves it, so 40 to 60% of perfectly lawful EU data gets thrown away on a Reject click.

Layer 3: the CMP is itself a third-party script. This is the one that stings. uBlock Origin and Brave block CMP scripts for 30 to 40% of EU users. On single-page apps the banner races the page transition and loses. When the CMP script is blocked, no banner renders, no consent is captured, and you usually do not get a fallback either. A CMP cannot solve the problem of being itself the thing that gets blocked.

Layer 4: bot contamination. 24 to 31% of recorded sessions are bots. A CMP has no [bot filtering](/fraud-traffic-validation), so its own consent-rate dashboards count bot interactions as consent decisions. PillarlabAI ran a honeypot signup form in 2025: 3,000 signups, 77% fraudulent, 650 accounts on a single device fingerprint. Those bots interact with consent banners too, quietly inflating every "accept rate" report.

Layer 5: that contaminated data trains [Meta](/meta-conversion-api) and Google to find more bots, and [ROAS](/resources/facebook-roas-improvement-guide-from-black-box-to-profit-engine) degrades. A CMP does not touch the ad-signal pipeline at all.

So when you read "where it breaks" below, that is the lens. A pure CMP genuinely cannot fix Layers 1, 4, or 5, and that is fine, because that is not its job. What matters is whether it handles Layers 2 and 3 honestly, and whether the brand sells it as more than it is. The root cause across the whole market is the same: third-party scripts collecting mixed data with no isolation before it leaves your infrastructure. The architectural fix is first-party, filtered, two tiers separated at source.

## CMP rankings, by real value for money

Tiered by what you actually get for what you actually pay. DataCops sits at the top of its tier because it solves the structural layer a CMP cannot. The rest are ranked as CMPs, fairly.

### Tier 1: the architectural layer

**DataCops.**

**What it is:** not a CMP in the banner sense. It is a first-party data collection layer that runs on your own subdomain.

**What it does well:** it closes the layers a CMP structurally cannot. Because collection is first-party rather than a third-party script, it is far more resilient to the blocking that kills CMP banners (Layer 3). It splits data into two tiers at the source: anonymous analytics flow unconditionally and legally, identifiable data waits for consent, which means a Reject All click costs you the profile, not the whole session (Layer 2). Bot filtering runs at ingestion against a 361.8B-plus IP database, separating residential traffic from datacenter, VPN, proxy, and Tor (Layer 4). Clean conversion signal is what reaches Meta, Google, TikTok, and LinkedIn (Layer 5).

Where it breaks, honestly: DataCops is not a drop-in cookie banner, so if all you legally need is a TCF banner you will still pair it with one. It is a newer brand than [OneTrust](/alternative/onetrust-alternative) or [Cookiebot](/alternative/cookiebot-alternative), and SOC 2 Type II is still in progress, so a regulated enterprise buyer with a hard vendor checklist may need to wait. Shared [CAPI](/conversion-api) is in verification, not fully live. It surfaces data context; it does not promise a perfect 100% clean feed.

**Value for money:** 9/10 for any brand running paid ads on EU traffic, because it fixes the expensive layer the entire CMP market ignores.

**Pricing:** free tier includes 2,000 signup verifications a month; paid tiers scale from there.

### Tier 2: best-value CMPs that do the job well

**Borlabs Cookie.**

**What it is:** the dominant German-market WordPress consent plugin.

**What it does well:** it physically rewrites the page's HTML to block third-party scripts before they load, delivers clean Google Consent Mode v2 signaling, and has a four-year-plus track record of staying current with EU rules including IAB TCF v2.3.

**Where it breaks:** it is WordPress-only, so [Shopify](/resources/best-shopify-capi-tools-2026), Magento, BigCommerce, and headless users cannot touch it. On Layer 3 it is better than most, because it loads from your own server rather than a third-party CDN, which substantially cuts the script-failure risk, though aggressive blockers targeting CMP patterns can still catch it. Layers 4 and 5 are outside its scope, which is fine for a consent plugin. The real-world snag: with 67% of Consent Mode v2 setups non-compliant, Borlabs gives you the right tool but the default config guides are thin for non-technical owners. Pricing is also reported inconsistently across aggregators, which breeds distrust.

**Value for money:** 8/10.

**Pricing:** annual license, €39 for one site up to €299 for 99 sites, updates and support included.

**Enzuzo.**

**What it is:** an all-in-one that bundles a consent banner, privacy policy generator, and data subject request management.

**What it does well:** it covers three compliance jobs in one platform at [pricing](/pricing) roughly 80% below OneTrust, with Google CMP Gold certification and Microsoft Consent Mode support.

**Where it breaks:** it is a CDN-hosted banner, so Layer 3 hits it directly: uBlock blocks it for 30 to 40% of EU users before it renders, and Enzuzo has published a lot about browser privacy changes but has not built a first-party or inline-script option to dodge that. The DSR automation small businesses actually need sits behind a 17x price jump, from the $9 plan to the $150 Mid-Market tier. The $59 PLG Pro plan caps at 10 domains, which mid-market sites with regional subdomains routinely blow past.

**Value for money:** 7/10, best all-in-one value below enterprise, with a real CDN blind spot.

**Pricing:** Starter $9/month ($7 annual), Growth $29, PLG Pro $59 annual, Mid-Market from $150. Free version available.

**Sirdata.**

**What it is:** a publisher-focused CMP with a pricing model nobody else offers.

**What it does well:** publishers who join Sirdata's data partnership get the CMP free, in exchange for audience data access. No other vendor here can offset its own cost like that.

**Where it breaks:** ABconsent is a client-side script, so Layer 3 applies, no server-side fallback published. The data-monetization model itself raises a Layer 4 question, because it monetizes consenting-audience data and that audience is partly bots inflating the consent counts. The free-for-data model also creates a possible [GDPR](/resources/best-gdpr-consent-tool-2026) conflict of interest a regulator could question: is the banner designed for user autonomy or for maximizing data-access consent? And it is publisher-only, a poor fit for ecommerce or lead-gen.

**Value for money:** 7/10 for qualifying publishers, 5/10 for everyone else.

**Pricing:** from €25/month for 50,000 hits; free for publishers who qualify for the data partnership.

**CookieFirst.**

**What it is:** a pageview-priced CMP with a clean UI and a forgiving billing model.

**What it does well:** Google Consent Mode v2 and IAB TCF v2 support, and a soft-limit model, 250K pageviews with a 25% grace buffer, so small and mid-market sites get predictable bills without hard cutoffs.

**Where it breaks:** CDN-hosted, so Layer 3 applies, the banner silently fails for 30 to 40% of blocker users. A subtler issue: because it bills per pageview and counts bot-generated pages too, brands with heavy crawler traffic climb pricing tiers faster than their human audience grows. It was acquired by iubenda (team.blue) in January 2025, and the roadmap is now a multi-brand committee decision, so feature velocity has visibly slowed.

**Value for money:** 6/10, best price-to-compliance ratio among CDN-hosted CMPs.

**Pricing:** from €9/month per domain, pageview-based, enterprise custom.

**CookieHub.**

**What it is:** a well-documented CMP with session-based tier pricing.

**What it does well:** clean UI, strong customization toolkit, Google Consent Mode v2 support, and a 2026 pricing restructure that replaced per-session overage fees with automatic plan upgrades, killing surprise bills.

**Where it breaks:** CDN-hosted, so Layer 3 applies, when uBlock blocks it the banner never renders and the site sits in a no-consent-obtained grey zone. The April 2026 restructure grandfathered legacy plans only to June 30 then auto-migrated them on July 1, which moved some sites to higher tiers without an explicit opt-in. Multi-domain pricing is per-domain with no bundle discount, so a 50-domain deployment gets no economy of scale. Consent Mode v2 also needs manual [GTM](/resources/advanced-gtm-server-side-tracking-for-google-ads) tag work the tool does not auto-configure.

**Value for money:** 6/10.

**Pricing:** free up to 1,000 sessions/month; paid from about $5.38/month per domain.

**Secure Privacy.**

**What it is:** a competitive mid-market CMP with the most transparent per-domain pricing in its tier.

**What it does well:** plans from $14/month, a genuine 30-day free trial, coverage for GDPR, CCPA, LGPD, and IAB TCF v2.2, plus automated compliance reporting that compliance-team buyers like.

**Where it breaks:** it loads via CDN script, so Layer 3 applies like every CDN-hosted CMP, and it does not publish delivery-failure telemetry. The Layer 4 problem is sharper here than for most, because automated compliance reporting is a headline feature, and those reports count consent rates that include bot interactions. A DPA audit asking whether "accepted" signals from automated crawlers count as valid GDPR consent would find that weakness. Per-domain pricing also stacks: a brand with 8 regional domains pays $1,600-plus a month at the enterprise tier. Support response on non-enterprise tiers averages 48-plus hours per G2 reviews.

**Value for money:** 6/10, honest transparent pricing is a real advantage.

**Pricing:** free plan; paid $14 to $199/month per domain, all paid plans include the 30-day trial.

**ConsentManager.**

**What it is:** an IAB TCF v2-certified, Google-certified CMP with automated cookie scanning and granular consent logs.

**What it does well:** the Professional tier covers up to 20 websites and 10M pageviews, which is genuinely cost-effective for agencies.

**Where it breaks:** CDN-hosted banner listed on uBlock filter lists, so Layer 3 applies, when blocked you get neither consent nor a fallback. The auto-blocker fires off cookie-category assignments that must be manually maintained, so adding a new marketing tag in GTM without updating the cookie audit means it runs unconsented, a common gap. CDN hosting also means a Cloudflare outage or a filter-list update can silently break consent collection across all your sites at once with no alerting. It is now one of four CMP brands under iubenda/team.blue, so roadmap prioritization is shared.

**Value for money:** 6/10, solid TCF-certified CMP at a fair agency price.

**Pricing:** free up to 3,000 views/month; Standard €53/month for 1M pageviews; Professional €219/month.

**InMobi CMP (formerly Quantcast Choice).**

**What it is:** the long-time default free TCF CMP for ad-supported publishers.

**What it does well:** it is free, and that zero-cost model made it the go-to for SMB publishers who needed IAB TCF consent strings without a budget.

**Where it breaks:** it is the textbook Layer 3 failure, it IS the third-party CMP script on a CDN, blocked by uBlock and Brave in 30 to 40% of sessions, and a free tool cannot remediate itself. As a free product it has no SLA and no support tier, so publishers absorb 100% of the data-loss risk silently. Quantcast sold it to InMobi in August 2023; the rebrand broke integration docs and delayed support, and the mobile SDK was deprecated.

**Value for money:** 5/10, free is compelling but it is structurally the weakest link.

**Pricing:** free; enterprise support packages exist but are not publicly priced.

### Tier 3: enterprise privacy platforms (priced well out of "affordable")

These are not affordable CMPs and I am not pretending they are. They are here because they show up in CMP comparisons and you should know why they do not belong in a budget shortlist.

**Privado.**

**What it is:** a privacy compliance and data-mapping platform.

**What it does well:** it continuously scans your first-party code and third-party scripts to auto-generate data maps and flag non-compliant data flows before they ship, and its October 2025 AI Agents release can auto-populate privacy assessment forms from documentation. Genuinely useful for privacy engineers and DPOs.

**Where it breaks:** on Layer 3 it detects when a banner or pixel mis-fires, which is useful, but it surfaces the problem without fixing it. It does no bot filtering (Layer 4) and never touches the ad pipeline (Layer 5), so bot-contaminated, consent-gated data passes a Privado audit with flying colours. It tells you collection is lawful, never whether the data is real. Pricing is enterprise-quote-only with no public numbers, so mid-market teams hit a sales wall immediately.

**Value for money:** 6/10.

**Pricing:** enterprise quote only; comparable tools run $20,000 to $80,000/year.

**Transcend.**

**What it is:** an enterprise privacy automation platform combining consent management, data mapping, and DSR fulfillment.

**What it does well:** it handles Reject All signal propagation properly (Layer 2 addressed at the consent layer, better than most), and the full privacy-ops stack is genuinely complete.

**Where it breaks:** its own consent script loads from a third-party CDN and is on privacy ad-blocker lists, so Layer 3 hits it as hard as OneTrust, 30 to 40% of EU users never get a valid prompt, and a blocked Transcend script means no consent gate at all. The price floor is $10,000/year, entirely out of reach for the SMB and mid-market teams who make up most GDPR-affected businesses. DSR automation across hundreds of integrations takes weeks of implementation, not the advertised set-and-forget.

**Value for money:** 6/10.

**Pricing:** from $10,000/year, full pricing custom.

**Osano.**

**What it is:** a CMP with a contractual no-fine guarantee.

**What it does well:** up to $500K of coverage for regulatory penalties when fully implemented on a qualifying paid plan, plus transparent published pricing for the consent module and a data-breach monitoring layer.

**Where it breaks:** the banner is a CDN-hosted client-side script, so Layer 3 applies, and [Osano](/alternative/osano-alternative) relies on client-side JavaScript to dispatch consent signals, meaning the same ad blocker that hides the banner also stops the signal reaching GTM. On Layer 2 it fires the rejection signal and recovers nothing, so the no-fine guarantee covers the penalty risk but not the business cost of the 40 to 60% of rejecting EU visitors whose lawful anonymous data is simply lost. The guarantee also has stringent conditions: the $199/month Plus tier is not covered, so the headline benefit is out of reach for most SMB buyers.

**Value for money:** 6/10.

**Pricing:** cookie consent Plus tier $199/month; broader plans custom.

**DataGrail.**

**What it is:** a privacy-ops platform built around DSR automation.

**What it does well:** it integrates with 2,000-plus SaaS connectors to auto-fulfill GDPR and CCPA access, deletion, and portability requests without manual analyst hours. Strong for regulated mid-market and enterprise drowning in deletion requests.

**Where it breaks:** it operates on stored data records, not the live session layer. It integrates with third-party CMPs rather than replacing them, so if the CMP script is blocked DataGrail gets no consent signal and has no fallback (Layer 3 inherited, not solved). Anonymous post-rejection traffic is invisible to it (Layer 2 untouched). The 2,000-plus connector claim includes many shallow read-only connectors; real deletion automation needs deeper per-connector work. Pricing is custom-quote-only, typically $30K to $80K/year mid-market.

**Value for money:** 6/10, excellent for DSR pain, weak for analytics or signal quality.

**Pricing:** custom quote only.

**Didomi.**

**What it is:** the strongest enterprise preference-management platform in Europe.

**What it does well:** granular consent purposes, multi-regulation orchestration across GDPR, CCPA, and LGPD, and a preference center that persists user choices across sessions.

**Where it breaks:** Didomi IS the CMP script, CDN-hosted, blocked by uBlock and Brave, no server-side fallback and no published block-rate telemetry (Layer 3). On Layer 2 it captures and signals rejection correctly but routes zero anonymous session data, leaving the analytics blind spot for 40 to 60% of EU users wide open. Bot interactions inflate its own consent-given counts (Layer 4). It acquired Sourcepoint in July 2025 with a two-year integration timeline, so Sourcepoint customers face platform uncertainty. Enterprise pricing is opaque and quote-only, with agency partners reporting 20 to 35% renewal increases.

**Value for money:** 6/10.

**Pricing:** custom quote only; reported €30K to €150K/year.

**Sourcepoint.**

**What it is:** a CMP known for the most sophisticated consent UI testing layer in the market, acquired by Didomi in July 2025.

**What it does well:** A/B testing of consent banners, accept-rate analytics, CCPA opt-out flows at enterprise publisher scale.

**Where it breaks:** CDN-served client-side script, so Layer 3 applies, no server-side fallback. Its signature A/B banner-testing feature has no bot filtering, so Layer 4 contaminates it directly, accept-rate "wins" in banner experiments partly reflect bot behaviour, which can invalidate the statistical conclusions the feature exists to produce. On top of that, the Didomi acquisition leaves 200-plus enterprise clients on a platform being absorbed over 24 months with undisclosed pricing and reports of 30%-plus renewal increases.

**Value for money:** 4/10 currently, acquisition uncertainty makes new purchases high-risk.

**Pricing:** undisclosed post-acquisition.

**TrustArc.**

**What it is:** an enterprise CMP that, with OneTrust, dominates Fortune-500 procurement.

**What it does well:** automated DSAR workflows, Google CMP Gold certification achieved in Q4 2025, and a deep privacy-governance suite covering data inventory and assessments.

**Where it breaks:** TrustArc is itself the third-party script that fails (Layer 3), 30 to 40% of EU visitors on Brave or uBlock never see the banner, never fire a consent signal, and TrustArc does not know or report on it. It fires the reject signal and preserves no anonymous session data (Layer 2). It has no bot or IVT filtering, so consent records are generated per session regardless of whether the session is human (Layer 4). Pricing starts at $15,000 to $40,000/year for 1 to 5 domains and routinely passes $100,000/year with DSAR and multi-domain modules. Main Capital Partners acquired it in October 2025, adding renewal uncertainty.

**Value for money:** 4/10, mid-market buyers pay Fortune-500 prices for a tool that still cannot tell them how many users saw the banner.

**Pricing:** $15,000 to $40,000/year and up, custom.

**Securiti.**

**What it is:** a comprehensive data and AI governance platform.

**What it does well:** data discovery, DSPM, privacy-ops, and AI trust controls in one platform, and post-Veeam acquisition it pairs data resilience with governance at a scale no other vendor matches.

**Where it breaks:** it integrates with third-party CMPs rather than replacing them, so it inherits all of Layer 3's CDN-blocking exposure without solving it. It does not filter bots from live analytics (Layer 4) and has no ad-platform connection (Layer 5). It governs data after it enters enterprise systems, never the quality of data before it gets there. Veeam completed its $1.725B acquisition in December 2025, so roadmap and pricing are in transition. Custom-quote-only pricing, with pre-acquisition contracts reported at $80K to $500K/year.

**Value for money:** 5/10, exceptional breadth, prohibitively expensive if your real problem is analytics data quality.

**Pricing:** custom quote only.

**BigID.**

**What it is:** a comprehensive enterprise data privacy platform.

**What it does well:** AI-powered data discovery across 1,000-plus classifiers and 100-plus data sources, automated GDPR Article 17 deletion workflows, consent management, and DSPM in one auditable system. Its November 2025 CMP Express adds a standalone consent banner deployable in under 24 hours, and on Layer 3 that lighter, potentially self-hosted option is a genuine step toward addressing the third-party-script failure.

**Where it breaks:** BigID is a data governance platform, not a tracking tool, so it contributes nothing to data collection quality, bot filtering, or ad-signal hygiene (Layers 1, 4, 5). Pricing starts at $175,000/year, structurally inaccessible to anyone below large enterprise, and it needs a dedicated privacy engineering team and a 3-to-6-month implementation before it delivers value.

**Value for money:** 6/10 for the enterprises it is built for, irrelevant for a budget CMP search.

**Pricing:** from $175,000/year; CMP Express pricing not publicly confirmed.

## Decision guide

WordPress site, want the cheapest credible compliant banner: Borlabs Cookie, and you get first-party hosting as a bonus.

Need a consent banner, a privacy policy, and DSR handling in one cheap tool: Enzuzo, just budget for the Mid-Market tier if you need DSR automation.

Ad-supported publisher with no budget at all: InMobi CMP is free, but accept that you carry the blocking risk silently.

Publisher willing to trade audience data for a free CMP: Sirdata's data partnership.

Want predictable pageview-based billing with no surprise overage: CookieFirst's soft-limit model or CookieHub's auto-upgrade model.

Compliance team that wants transparent per-domain pricing and audit reports: Secure Privacy, but do not trust the consent-rate numbers as human-only.

Agency managing many sites: ConsentManager's Professional tier covers 20 sites economically.

Large enterprise with a dedicated privacy team and a real budget: TrustArc, Didomi, BigID, or Securiti, depending on whether your priority is consent, preference management, or full governance.

Running paid ads on EU traffic and tired of the data being a mix of bots and missing humans: a CMP alone will not fix that. You need first-party collection with two data tiers. DataCops.

## You bought a banner. You did not buy a data layer.

The mistake almost everyone makes shopping for an "affordable CMP" is thinking the banner is the data solution. It is not. The cheapest CMP and the most expensive one both stop at the same wall. They capture a consent decision, and then a third of your EU visitors block the script that was supposed to capture it, and the banner you paid for never even rendered for them.

Affordability is real and worth optimizing. Pick the cheapest CMP that genuinely covers your traffic tier and your platform. But do not confuse a cheap banner with a clean data pipeline. The banner is the legal checkbox. The data underneath it, what it captures, what it misses, how much of it is bots, is a separate question your CMP price never touches.

So here is the audit. Open your own consent dashboard. What is your reported accept rate? Now ask the two questions the dashboard cannot answer: how many of your EU visitors never saw the banner at all because their browser blocked the script, and how many of those "accept" clicks came from a bot? If you do not know either number, you are not measuring consent. You are measuring the visitors who let you measure them.

---

Research by [DataCops](https://www.joindatacops.com) — first-party tracking, consent infrastructure, fraud prevention, and server-side CAPI for Meta, Google, TikTok, and LinkedIn.
