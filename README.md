# bright data web unlocker: what it costs, where it wins, and when a cheaper ScraperAPI plan will do

Bright Data's Web Unlocker is the company's managed unblocking API: you send a URL, and it handles proxy selection, IP rotation, JavaScript rendering, CAPTCHA solving and retries before returning the page's raw HTML or JSON. It's built for one job — getting pages from sites that actively fight scrapers — and independent testing suggests it does that job about as well as anyone in the market right now.

The catch is pricing. Web Unlocker is priced per successful request with no cheap flat subscription, and Bright Data requires KYC verification before you can start. That combination is exactly why a lot of searches for this product end up on comparison pages: people want to know whether they actually need the premium tool, or whether a simpler scraping API covers their use case at a fraction of the cost. This piece covers both sides, with the numbers.

> **Quick take:** if you're scraping Cloudflare- or DataDome-protected sites at scale, Bright Data's Web Unlocker is the stronger tool — independent benchmarks put its success rate around 95–98%, and it bills mainly on successful delivery. If your targets are mostly ordinary pages or e-commerce sites, ScraperAPI starts at **$49/month (100,000 credits)** with a permanent free tier, a 7-day trial of 5,000 credits, and a 7-day no-questions-asked refund. Most readers in that second camp don't need the premium option — 👉 [check ScraperAPI's current plans and prices](https://www.scraperapi.com/pricing/?fp_ref=coupons) to see where your volume lands.

## What Bright Data's Web Unlocker actually does

It's an HTTP-based unlocking proxy that automatically picks the best proxy network for each request, handles anti-bot protections, solves CAPTCHAs, and retries failed attempts on your behalf. Under the hood you send a single POST request to Bright Data's API endpoint with a zone name, the target URL, and a format setting; what comes back is the target page's HTML or JSON. No proxy orchestration, no browser automation to maintain.

The features list explains why the product has a reputation. It handles JavaScript rendering, manages cookies and sessions, and rotates IPs automatically. It's designed to work against the major anti-bot systems — Cloudflare, DataDome, PerimeterX — and Bright Data sells dedicated CAPTCHA solver pages for specific systems like DataDome, Yandex SmartCaptcha and puzzle-type captchas, with 5,000 requests per month free on those solvers.

How well does it work in practice? One benchmark covering 11 unblocking providers ranked Bright Data's Web Unlocker highest with a **98.44% success rate**, and independent testing generally places it in the 95–98% range on protected sites. One of the comparison sources for this piece notes that Bright Data's own "98%, close to 100%" marketing claim is on the optimistic side but unusually holds up under third-party testing. For context, Proxyway's independent testing put ScraperAPI's overall success rate around 62–64% — the gap shows up almost entirely on heavily defended targets.

There's also a compliance detail worth knowing before you sign up: Bright Data enforces KYC (identity verification) that can take up to 3 business days. The company was founded in 2014 as Luminati Networks and was sold to London private-equity firm EMK Capital in 2017; the strict onboarding is a compliance signal rather than a red flag, but it does mean you can't start scraping the minute you sign up.

## What the Web Unlocker costs

Bright Data does not sell Web Unlocker as a flat monthly plan. You pay per successful request, with third-party breakdowns listing it around **$1.50 per 1,000 requests** in one teardown, though several 2026 price roundups put it closer to **$3 per 1,000 requests** ($3.06/1,000 in one detailed 2026 comparison). That spread matters, so treat both numbers as an estimate range and check the live pricing page before committing — Bright Data adjusts prices often.

The wider platform pricing gives you a sense of where the product sits:

| Bright Data product | Starting price |
| --- | --- |
| Web Unlocker | ~$3.06 / 1,000 requests |
| SERP API | $2.85 / 1,000 requests |
| Residential proxies | ~$5.04/GB (down to ~$2.50/GB on committed plans) |
| Minimum commitment | ~$500/month |

Two things stand out. First, there's no entry-level subscription — the residential committed plans start around $1,999/month, and the practical floor for using the platform seriously is roughly $500/month. Second, because pricing is per-request with volume-based compression, Bright Data gets cheaper at high volumes, which is why one 2026 comparison concludes it's the better deal at 1M+ pages/month while ScraperAPI is cheaper under about 500K pages/month.

One billing nuance that works in Bright Data's favor: Web Unlocker bills mainly on **successful delivery**. You're largely not paying for the failed attempts, retries, and CAPTCHA pages that consume attempts behind the scenes.

## The budget alternative: ScraperAPI's full plan list

ScraperAPI takes the opposite design bet. Everything Bright Data exposes to you — proxy networks, rotation logic, session handling — is abstracted behind a single endpoint. You send a URL (with an optional `render=true` for JavaScript rendering), you get back HTML or, for Amazon and Google-style targets, structured JSON. You can't route your own Selenium or Puppeteer scripts through it and you can't pick individual proxies. That's the trade for a $49 starting price and instant signup with no identity verification.

Here's the full plan list as shown on ScraperAPI's pricing page, with annual billing at 10% off:

| Plan | Price/mo (annual) | Credits/mo | Concurrent threads | Geo-targeting |
| --- | --- | --- | --- | --- |
| Free | $0 | 1,000 | 5 connections | — |
| Hobby | $49 ($44.10) | 100,000 | 20 | US & EU only |
| Startup | $149 ($134.10) | 1,000,000 | 50 | US & EU only |
| Business | $299 ($269.10) | 3,000,000 | 100 | Country-level |
| Scaling | $475 ($427.50) | 5,000,000 | 200 | Country-level |
| Professional | $975 ($877.50) | 10,500,000 | 300 | Country-level |
| Advanced | $1,975 ($1,777.50) | 21,500,000 | 500 | Country-level |
| Enterprise | Custom | 22,000,000+ | 500+ | Country-level |

Every paid plan includes the same core feature set: JS rendering, premium proxies, automatic retries, CAPTCHA and anti-bot detection, custom headers and sessions, unlimited bandwidth, and a 99.9% uptime guarantee. Paid tiers add premium residential and mobile IPs, advanced bypassing, structured data parsing APIs, DataPipeline and full crawler access.

The docs also mention a separate Student plan for eligible students; the pricing page doesn't list its numbers publicly, so check the documentation if that's you.

A worked cost comparison makes the positioning concrete: **100,000 simple requests per month costs $49 on ScraperAPI's Hobby plan, versus roughly $306 for the same volume on Bright Data's Web Unlocker** at $3.06/1,000. On plain and e-commerce pages, comparison writeups consistently find ScraperAPI delivers the lowest cost per delivered page of the two by a wide margin.

## The credit math most comparison posts skip

If you're comparing these two, one detail almost every ranking article leaves out is that ScraperAPI's "credits" are not all worth one request. The official pricing page states it plainly: a standard page costs 1 credit, **Amazon costs 5, Google and Bing (including subdomains) cost 25, and LinkedIn costs 30**. Pages behind Cloudflare, Datadome or PerimeterX add **10 credits per request** when ScraperAPI bypasses them. JavaScript rendering runs roughly 5–10 credits depending on the page.

That changes the arithmetic of every plan in the table above. A Hobby plan's 100,000 credits is 100,000 simple pages, but only about 20,000 Amazon pages, or around 4,000 Google searches, or roughly 9,000 requests against a bypassed Cloudflare site. One analysis of the free tier — where the same multipliers apply to the 1,000 monthly credits — points out that at 75 credits per rendered protected page, the free allowance covers about 13 pages a month.

Before you pick a plan based on raw credit counts, do two things in the dashboard: run your actual target URLs through the **Domain Cost Estimator**, which shows the exact credit cost for any URL, and set a `max_cost` per scrape so a single expensive request can't blow through your budget. Both are built in, and using them is the difference between a plan that fits and one that runs dry two weeks in. 👉 [compare all ScraperAPI plans and run your own cost estimate](https://www.scraperapi.com/pricing/?fp_ref=coupons) before committing to a tier.

## Where the price gap flips: success rate and billing model

Here's the part that keeps Bright Data in business despite the $500/month floor. On sites that don't fight back, paying Web Unlocker prices is, in the words of one comparison, "pure waste." But on a Cloudflare-protected page the math inverts.

ScraperAPI's failure rate on heavily defended targets means a meaningful share of your billable requests return nothing usable — one source describes it as roughly one failure in three, and notes ScraperAPI can bill a CAPTCHA page as a delivered result. Bright Data's Web Unlocker, by contrast, lands the page far more often and bills mainly on successful delivery. Multiply cost per attempt by the number of attempts you actually need, and the real-world gap on protected targets shrinks sharply. It doesn't disappear — Bright Data is still the premium option — but the sticker comparison of $49 vs ~$500 undersells what you get on hard targets.

So the honest decision rule looks like this:

- Mostly standard pages, e-commerce endpoints, light-to-moderate protection → ScraperAPI's per-credit plans are dramatically cheaper, and the built-in anti-bypass handles the middle ground.
- Heavy Cloudflare/DataDome/PerimeterX targets, or high volume where Bright Data's per-request pricing compresses → the Web Unlocker's 95–98% success rate and per-success billing justify the premium.
- You need raw proxy access for your own Selenium/Puppeteer/Playwright scripts → only Bright Data offers that; ScraperAPI has no direct proxy access at all.

## Hidden billing mechanics worth knowing before you buy

Neither company's landing pages make the overage rules easy to find, and they're exactly what determines whether a "cheap" plan stays cheap. ScraperAPI's documented mechanics:

1. **Running out of credits pauses scraping by default** — it doesn't silently bill you.
2. **Auto-Upgrade** (opt-in, on Hobby through Professional monthly plans) automatically bumps you to the next tier when credits run out, usually at a better price per credit.
3. **Pay-As-You-Go** is available on Scaling, Professional, Advanced and Enterprise: you keep scraping past your limit at a fixed per-credit rate. Critically, you can set a **monthly spending cap**, and the service will not exceed it unless you change the setting yourself — the official docs are explicit that this is a spending limit, not a pre-charged amount. If you've ever been burned by surprise proxy overage bills, this is the detail to look for.
4. **Concurrency limits return a 429**, not a queue. Rejected requests don't get billed; you retry after dropping back under your thread limit.
5. **Annual plans** can renew early for a fresh batch of credits if you burn through the yearly allowance.
6. Billing is per request, never per bandwidth, and you can't buy individual IPs from the pool.

The concurrency cap is worth a second look if you're coming from Bright Data, where concurrency scales with plan tier without hard thread counts. On ScraperAPI, a Hobby plan's 20 concurrent threads is a real ceiling — exceed it and you get 429s until you throttle down or upgrade. 👉 [see the full plan tiers and thread limits on the pricing page](https://www.scraperapi.com/pricing/?fp_ref=coupons) if concurrency is your binding constraint.

## Trials, refunds, and how risk-free each one is

ScraperAPI's trial terms are unusually generous and confirmed in its own documentation: every new account gets **7 days with 5,000 API credits, no credit card required**, plus a permanent free plan of 1,000 credits per month with up to 5 concurrent connections. If you need more test volume, support can grant additional credits. On top of that, there's a **7-day no-questions-asked refund policy** — contact support and they process it — and you can cancel anytime from the dashboard without being charged. Bright Data also offers a 7-day trial, but pair it with the KYC wait and the lack of a small flat plan, and the practical difference is stark: with ScraperAPI you can be running your first real test in minutes, while with Bright Data you may spend up to three business days in verification first.

If you want to test rather than read another comparison table, 👉 [start the 7-day free trial with 5,000 credits](https://www.scraperapi.com/?fp_ref=coupons) and point it at your actual target sites — that's a better predictor than any benchmark run on someone else's target list.

## FAQ

**Is Bright Data legit?**
Yes. It was founded in 2014 as Luminati Networks, sold to EMK Capital in 2017, and is headquartered in Tel Aviv. Its strict KYC process is a compliance feature, and the company compensates billing errors generously with credits, according to third-party reviewers.

**Can I use ScraperAPI as a proxy?**
No. ScraperAPI has no raw proxy access — you can't point your own scraper tooling at its IP pool or control rotation and sessions yourself. If direct proxy access is a requirement, that's a genuine reason to look at Bright Data's platform instead.

**How hard is it to switch between the two later?**
Easy in one direction. Since ScraperAPI is a single-endpoint API, migrating to Bright Data's Web Unlocker involves changing API calls in your code, and the integration pattern (send URL, get HTML) is similar. Moving the other way is also straightforward at the API level, but you'd lose raw proxy access in the process.

**Does ScraperAPI work on heavily protected sites?**
It has built-in anti-bot detection and advanced bypassing on paid plans, and independent testing puts its overall success rate around 62–64% — fine for most targets, but noticeably behind Bright Data on Cloudflare and DataDome pages, where users have reported outright 500 errors. For those specific targets, budget for the premium tool or accept a higher failure rate.

## Which one should you actually pick

Match the tool to your targets, not to the marketing:

- **Scraping standard pages, Amazon product data, or moderate-volume SERP work under ~500K requests/month:** ScraperAPI's Hobby ($49) or Startup ($149) plans will cost you a small fraction of the Bright Data equivalent, and the 7-day refund window means you can validate against your own targets first.
- **Scaling past a few million requests/month on ordinary sites:** compare Business ($299, 3M credits) against Web Unlocker's volume pricing, but watch the credit multipliers — if your targets skew toward Google and LinkedIn, your effective per-request cost climbs fast.
- **Heavy Cloudflare/DataDome targets, enterprise volume, or you need raw proxy access for custom scripts:** Bright Data's Web Unlocker earns its price there; don't force ScraperAPI to do a job its success rate can't support.

Before you commit to anything, run your five most important target URLs through ScraperAPI's Domain Cost Estimator during the trial — if they come back at 1–5 credits each, the cheap plan is real; if they're 25–30 each, do the math on the premium option instead. Either way, you can 👉 [open your ScraperAPI account and start with 5,000 free credits](https://www.scraperapi.com/?fp_ref=coupons) today and have actual data by tonight.
