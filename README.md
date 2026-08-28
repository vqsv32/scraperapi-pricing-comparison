# Website Crawler API: What It Actually Is, How ScraperAPI Solves the Hard Parts, and Which Plan Is Right for You — Credits Explained, Real Costs Calculated, and Every Plan Compared

So you've decided you need a website crawler API. Maybe you've been writing scraper code for a few weeks, and it works fine locally — clean HTML, data flows into your spreadsheet, life is good. Then you push it to production and watch it die in real time: IP bans, CAPTCHAs, 403s, JavaScript pages that return blank HTML. The whole thing that took days to build starts failing on the third request.

That's the moment most developers realize they're not actually in the scraping business — they're in the *infrastructure* business. Proxies, headless browsers, retry logic, session management. It compounds fast.

A website crawler API is the thing that takes that entire layer off your plate.

---

**What Is a Website Crawler API, and Why Does It Exist?**

At its most basic level, a website crawler API is a proxy layer you call instead of the target website directly. You send it a URL; it routes your request through managed infrastructure, handles whatever anti-bot systems the site throws at it, and returns the HTML (or parsed data, depending on the service). You stop thinking about proxies. You stop thinking about CAPTCHAs. You just get the content.

The demand for this kind of service has exploded. The web scraping API market is currently a $2+ billion industry growing at 14–18% CAGR. Why? Because more companies are building data pipelines, market intelligence tools, price monitoring systems, and AI training datasets — and they've all run into the same wall. The web was not built to be scraped at scale, and websites have gotten aggressive about blocking it.

Building your own proxy rotation infrastructure from scratch takes weeks and costs real money to maintain. A website crawler API solves this in an afternoon.

**ScraperAPI** is one of the most widely used tools in this space. It launched in 2018, is headquartered in Las Vegas, and now processes 36 billion API requests per month for over 10,000 brands — including Deloitte, Sony, and Alibaba. The pitch is simple: one API endpoint, handles everything.

👉 [Try ScraperAPI free — no credit card required](https://www.scraperapi.com/?fp_ref=coupons)

---

**How ScraperAPI Actually Works**

The core product is one HTTP endpoint. You send a URL with your API key, and ScraperAPI routes it through their managed proxy pool — automatically rotating IPs, solving CAPTCHAs, and returning the HTML your code expects.

python
import requests

payload = {
    'api_key': 'YOUR_API_KEY',
    'url': 'https://example.com/product-page',
    'render': 'true',
    'country_code': 'us'
}

response = requests.get('http://api.scraperapi.com/', params=payload)
print(response.text)


That's the whole integration. No proxy credentials to rotate manually, no headless browser to spin up, no CAPTCHA service to wire in separately.

Under the hood, you get:

- **Proxy rotation** across 20M+ rotating datacenter and residential IPs across 30+ countries
- **JavaScript rendering** via headless Chrome — handles SPAs and dynamically loaded content
- **Automatic CAPTCHA solving** built into every request
- **Anti-bot bypass** — automatic detection and handling for Cloudflare, DataDome, and PerimeterX
- **Geotargeting** — send the `country_code` parameter to route requests through a specific country
- **Sticky sessions** — use `session_number` to reuse the same IP across multiple requests
- **97% average success rates** on standard rotating proxy pools
- **99.9% uptime SLA** across all plans

It also has a library of **18 structured data endpoints** — for Amazon, Google, Walmart, eBay, and Redfin — that return parsed JSON instead of raw HTML. More on those later.

---

**The Credit System: The Most Important Thing to Understand Before You Sign Up**

Here's where a lot of developers get burned. ScraperAPI advertises plans by total API credits per month — but "1 request = 1 credit" is only true for the simplest case. In practice, the credit cost per request depends on two variables that stack multiplicatively: the **target domain** and the **feature flags** you enable.

**Domain-based credit costs (automatic — you can't opt out):**

| Target Site Type | Credits per Request |
| --- | --- |
| Standard website (blog, news, etc.) | 1 |
| E-commerce (Amazon, Walmart, eBay) | 5 |
| SERP (Google, Bing) | 25 |
| Social media (LinkedIn) | 30 |

**Feature flag add-ons:**

| Parameter | Extra Credits |
| --- | --- |
| `render=true` (JavaScript rendering) | +10 |
| `screenshot=true` | +10 |
| `premium=true` (residential proxy) | +10 |
| `ultra_premium=true` | +30 |

Here's the part that catches people off guard: **combining features costs more than the sum of the parts.** Premium proxy (+10) plus JS rendering (+10) should logically be +20 — it's actually **+25**. Ultra-premium (+30) plus JS rendering (+10) should be +40 — it's actually **+75**.

So a Hobby plan ($49/month) with its 100,000 credits might sound generous. But if you're scraping Cloudflare-protected sites with JavaScript rendering, each request burns 75 credits. That 100,000-credit plan is actually **1,333 actual page requests** — about $36.75 per 1,000 pages.

Run the math for your actual use case before committing to a tier.

---

**All ScraperAPI Plans — Full Comparison Table**

Below is every current plan available, with real pricing and what you actually get:

| Plan | Monthly Price | Annual Price (per mo) | API Credits | Concurrent Threads | Geotargeting | Pay-As-You-Go | Purchase Link |
| --- | --- | --- | --- | --- | --- | --- | --- |
| **Free** | $0 | — | 1,000 | 5 | No | No | [Start Free](https://www.scraperapi.com/?fp_ref=coupons) |
| **Hobby** | $49/mo | ~$44/mo | 100,000 | 20 | US & EU only | No | [Get Hobby Plan](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| **Startup** | $149/mo | ~$134/mo | 1,000,000 | 50 | US & EU only | No | [Get Startup Plan](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| **Business** | $299/mo | ~$269/mo | 3,000,000 | 100 | 50+ countries | No | [Get Business Plan](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| **Scaling** | $475/mo | ~$427/mo | 5,000,000 | 200 | 50+ countries | ✅ Yes | [Get Scaling Plan](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| **Enterprise** | Custom | Custom | 5,000,000+ | 200+ | 50+ countries | ✅ Yes | [Contact Sales](https://www.scraperapi.com/contact-sales/?fp_ref=coupons) |

A few things to note about this table:

**Annual billing saves roughly 10–17%** depending on the tier. If you know you'll be scraping consistently for the next 12 months, the savings are real.

**Pay-As-You-Go only kicks in at Scaling ($475/month) and above.** On Hobby, Startup, and Business plans, if you exhaust your monthly credits before renewal, your service simply stops. You either upgrade to the next tier or wait. There's no "add credits for a fee" option at the lower tiers.

**Credits do not roll over.** Unused credits expire at the end of your billing cycle, every cycle.

**Geotargeting beyond US and EU requires the Business plan ($299/month) minimum.** If your project requires scraping from specific countries in Asia, Latin America, or elsewhere, you're looking at $299/month as your floor.

---

**Who Is Each Plan Actually For?**

The credit numbers are marketing. The real question is: what does your workload actually look like?

**Free plan** makes sense for evaluation. You get 1,000 credits per month, plus 5,000 credits during your first 7 days. Enough to test your target sites and figure out what multipliers apply to your use case. Do not build a production workflow on the free plan.

**Hobby ($49/month)** works well for small side projects and solo developers scraping standard websites — blogs, news aggregators, basic product research. If you're scraping plain HTML without JavaScript rendering and without premium proxies, 100,000 requests per month is genuinely useful. For JS-heavy sites, it shrinks to 10,000 rendered pages. For Amazon, it's 20,000 product pages.

**Startup ($149/month)** is the plan most growing projects land on. A million credits per month gives you serious room — 100,000 rendered pages, or 40,000 Amazon pages. The US & EU geotargeting limitation is the main friction point. If your use case is US or European market data, this plan handles it.

**Business ($299/month)** is where global projects start. Three million credits, 100 concurrent threads, and full 50+ country geotargeting. This is the minimum plan for any international data collection pipeline. If you're running a competitive intelligence tool, a price monitoring service, or any SERP tracking system with real volume, this is likely your starting point.

**Scaling ($475/month)** adds 5 million credits, 200 threads, and — crucially — the Pay-As-You-Go option. If you're building a production service where credit exhaustion mid-month would be a business problem, this tier gives you a safety net.

**Enterprise** is for teams processing tens of millions of requests. Custom credits, custom thread limits, dedicated support, SLA negotiation. 👉 [Talk to the sales team](https://www.scraperapi.com/contact-sales/?fp_ref=coupons) if you're at that scale.

---

**The Structured Data Endpoints: Skip the Parsing Work**

For the most commonly scraped platforms, ScraperAPI offers 18 pre-built structured data endpoints (SDEs) that return parsed JSON instead of raw HTML. These are available on all plans, including free.

**Amazon** (3 endpoints): Product details by ASIN, search results, competitor offers. Returns 18+ fields — price, ratings, BSR, images, variants, seller info, reviews — across 21 regional marketplaces.

**Google** (5 endpoints): SERP results (organic, ads, knowledge graph, People Also Ask, featured snippets, pagination), Shopping, Maps, News, and Jobs.

**Walmart** (4 endpoints): Product, Search, Category, and Reviews.

**eBay** (2 endpoints): Product and Search.

**Redfin** (4 endpoints): Search, Agent Details, Rental Properties, and For Sale listings.

These endpoints save serious development time — no HTML parsing, no selector maintenance when the site updates its layout. ScraperAPI claims 99.99% success rates on supported SDE domains.

The tradeoff: SDEs consume the same credit multipliers as regular requests. Amazon SDEs cost 5 credits each. Google SERPs cost 25. If you're running high volume, the math matters.

👉 [Explore ScraperAPI's structured data endpoints](https://www.scraperapi.com/?fp_ref=coupons)

---

**Where ScraperAPI Performs Well — and Where It Doesn't**

Not every website is equally scrapable, and ScraperAPI's performance varies significantly by target. Here's what independent benchmarks (Scrapeway, April 2026) found:

**Strong performance:**

| Target Site | Success Rate |
| --- | --- |
| Zillow | 100% |
| Etsy | 99% |
| Amazon | 98% |
| LinkedIn | 95% |
| Walmart | 93% |

Amazon, Google, Walmart, Zillow, and Etsy are ScraperAPI's core strengths. If your project lives in the e-commerce or real estate data space, it's genuinely reliable.

**Poor or zero performance:**

| Target Site | Success Rate |
| --- | --- |
| Realtor.com | 12% |
| Instagram | 0% |
| Booking.com | 0% |
| Twitter/X | 0% |

Social media is essentially a dead zone. If your data collection needs include Instagram, Twitter/X, or travel booking platforms, ScraperAPI is not the right tool. The documentation also explicitly forbids scraping behind login walls — no form-filling, no 2FA handling, no session auth.

One behavioral nuance worth knowing: ScraperAPI applies a **10-minute forced cache on difficult targets**. If you're tracking time-sensitive data like live pricing or inventory, you may receive data that's up to 10 minutes stale.

---

**How ScraperAPI Compares to Alternatives**

Since website crawler API is a crowded category, here's a realistic comparison at the ~$300/month tier:

**Basic HTML scraping (no rendering, standard sites):**

| Provider | Plan | Cost per 1K Pages |
| --- | --- | --- |
| ScrapingBee | Business $249 | $0.08 |
| **ScraperAPI** | **Business $299** | **$0.10** |
| Scrapfly | Startup $250 | $0.10 |
| ZenRows | Business $300 | $0.28 |
| Bright Data | PAYG | $1.50 |

**JavaScript rendering required:**

| Provider | Plan | Cost per 1K Pages |
| --- | --- | --- |
| ScrapingBee | Business $249 | $0.42 |
| Scrapfly | Startup $250 | $0.60 |
| **ScraperAPI** | **Business $299** | **$1.00** |
| ZenRows | Business $300 | $1.40 |
| Bright Data | PAYG | $1.50 |

ScraperAPI is price-competitive for basic HTML scraping and competitive (if not the cheapest) for JS rendering. Bright Data wins on advanced anti-bot handling and global proxy infrastructure at enterprise scale; Scrapfly and ScrapingBee edge it out on JavaScript rendering cost.

The honest verdict from the community: ScraperAPI is a solid proxy infrastructure layer for teams that already have scraper code. It's not a full platform — it doesn't offer hosted execution, scheduling, dataset storage, or workflow automation. If you need those things, tools like Apify fill that gap. If you just need a reliable proxy and rendering layer dropped in front of your existing code, ScraperAPI is hard to beat at the $49–$299 price range.

---

**Practical Tips for Getting the Most Out of ScraperAPI**

A few things that help in practice:

**Test your targets on the free tier first.** Use those 5,000 first-week trial credits to test your actual target sites — not test sites, not example.com. Find out what multipliers apply to your use case, estimate real monthly credit consumption, then choose a plan. Skipping this step is how you end up on the wrong tier.

**Disable premium features unless you need them.** ScraperAPI does NOT auto-enable `premium=true`, `ultra_premium=true`, or `render=true`. You control those. But domain-based pricing IS automatic — Amazon always costs 5 credits, Google always 25. Know this before you batch 100,000 URLs.

**Watch for the 404 billing quirk.** ScraperAPI charges credits for both 200 (success) and 404 (not found) responses. Failed requests due to ScraperAPI's own errors are not charged, but 404s from the target site are. Keep this in mind when scraping product catalogs with potentially dead links.

**Use SDEs when available.** For Amazon and Google specifically, the structured data endpoints save real engineering time. Even if the credit cost is the same, you're getting clean, structured JSON you don't have to parse.

**Set a calendar reminder to check your dashboard.** ScraperAPI has no proactive usage alerts — no email when you hit 80% of monthly credits, no notification before cutoff. You have to check manually. On Hobby and Startup plans, the analytics history only goes back 2 weeks.

👉 [Start your free trial with 5,000 credits](https://www.scraperapi.com/?fp_ref=coupons)

---

**The 7-Day Trial and Refund Policy**

ScraperAPI offers a 7-day free trial with 5,000 API credits — no credit card required to start. This is genuinely enough to test your actual production targets, run the credit multiplier math for your use case, and make an informed decision about which plan fits.

If you sign up for a paid plan and find it's not the right fit, there's a **7-day no-questions-asked refund policy**. Contact support within 7 days of purchase and you get your money back. That's a real safety net for teams evaluating multiple tools simultaneously.

Cancellation is also straightforward — you can cancel anytime from the dashboard without penalty. No lengthy cancellation flows, no hidden lock-in beyond the current billing period.

---

**Bottom Line: Is ScraperAPI the Right Website Crawler API for Your Project?**

If you're a developer or technical team with existing scraper code — Python, Node.js, Scrapy, Playwright — and you need a reliable, well-documented proxy and rendering layer, ScraperAPI earns its reputation. It's been doing this since 2018, processes tens of billions of requests a month, and the documentation is among the clearest in the category.

The credit multiplier system is the biggest gotcha. Run the numbers for your specific targets and feature flags before choosing a plan — not the headline credit numbers, the real credits-per-request for your actual workload.

If you're scraping Amazon at scale, tracking Google SERPs, monitoring Zillow listings, or collecting e-commerce data across major US retailers, ScraperAPI is genuinely excellent for those use cases.

If you need social media data, travel site data, or anything behind a login wall, you'll need a different tool for those targets specifically.

For teams starting fresh and unsure where to begin — the free plan with no credit card is the right first step. Five thousand credits in the first week is more than enough to answer every question you have before spending a dollar.

👉 [Get started with ScraperAPI for free — 5,000 trial credits, no credit card needed](https://www.scraperapi.com/?fp_ref=coupons)
