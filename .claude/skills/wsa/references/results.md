# Results Reference

## The Mindset
The deliverable is not a website. It is a website that performs.
Launch is when the job begins, not ends. No data = no proof = no retainer.

---

## GA4 Setup — Custom Events

Install GA4 measurement ID first. Then configure these events:

### Form Submission
```js
// Fire when any form submits successfully
gtag('event', 'form_submit', {
  form_name: 'contact',     // or 'newsletter', 'quote', 'booking'
  form_location: 'hero',    // or 'footer', 'popup', 'sidebar'
});
```

### Button / CTA Clicks
```js
document.querySelectorAll('[data-track]').forEach(el => {
  el.addEventListener('click', () => {
    gtag('event', 'cta_click', {
      button_text: el.innerText,
      button_location: el.dataset.track,
    });
  });
});
```

### Scroll Depth
```js
// Track when user reaches 25%, 50%, 75%, 90%
const depths = [25, 50, 75, 90];
const fired = new Set();
window.addEventListener('scroll', () => {
  const pct = Math.round((window.scrollY / (document.body.scrollHeight - window.innerHeight)) * 100);
  depths.forEach(d => {
    if (pct >= d && !fired.has(d)) {
      fired.add(d);
      gtag('event', 'scroll_depth', { percent: d });
    }
  });
});
```

### Phone Number Click
```js
document.querySelectorAll('a[href^="tel:"]').forEach(el => {
  el.addEventListener('click', () => {
    gtag('event', 'phone_click', { phone_number: el.href.replace('tel:', '') });
  });
});
```

### Outbound Link Click
```js
document.querySelectorAll('a[href^="http"]').forEach(el => {
  if (!el.href.includes(window.location.hostname)) {
    el.addEventListener('click', () => {
      gtag('event', 'outbound_click', { destination: el.href });
    });
  }
});
```

---

## GA4 — Conversion Setup

In GA4 → Admin → Events → mark these as conversions:
- `form_submit` (any form)
- `phone_click`
- `purchase` (e-commerce)
- Any event that = a lead or sale for this specific business

Verify in GA4 → Reports → Realtime while testing.

---

## Google Search Console Setup

1. Go to search.google.com/search-console
2. Add property → Domain method (requires DNS TXT record)
3. Submit sitemap: Settings → Sitemaps → add `https://yoursite.com/sitemap.xml`
4. Check after 3–5 days: Coverage report, Performance report
5. Bookmark: Performance → Queries (this is your keyword rank tracker)

---

## Heatmap Setup (Hotjar)

1. Create account at hotjar.com (free tier: 35 sessions/day)
2. Install tracking code in `<head>`:
```html
<script>
  (function(h,o,t,j,a,r){
    h.hj=h.hj||function(){(h.hj.q=h.hj.q||[]).push(arguments)};
    h._hjSettings={hjid:YOUR_SITE_ID,hjsv:6};
    a=o.getElementsByTagName('head')[0];
    r=o.createElement('script');r.async=1;
    r.src=t+h._hjSettings.hjid+j+h._hjSettings.hjsv;
    a.appendChild(r);
  })(window,document,'https://static.hotjar.com/c/hotjar-','.js?sv=');
</script>
```
3. Enable heatmaps on: Homepage, main service/product page, contact page
4. Enable session recordings for first 2 weeks post-launch
5. Alternative (free, no limits): Microsoft Clarity — clarity.microsoft.com

---

## Baseline Report — Capture at Launch

Save this as a dated document. This is your "before" for every future report.

```
## Launch Baseline Report
Date: [launch date]
URL: [site URL]

### Traffic
Organic sessions (last 30 days, if replacing existing site): [number]
Direct sessions: [number]
Source of data: [GA4 / previous platform]

### Search Performance (Google Search Console)
Total impressions (last 28 days): [number]
Total clicks (last 28 days): [number]
Average CTR: [%]
Average position: [number]
Top 5 queries: [list]

### Core Web Vitals (run at launch)
LCP (Largest Contentful Paint): [ms] — target: <2.5s
FID / INP (Interaction to Next Paint): [ms] — target: <200ms
CLS (Cumulative Layout Shift): [score] — target: <0.1
Tool: pagespeed.web.dev

### Conversions
Conversion rate on [key page]: [%]
Total goal completions (if applicable): [number]

### Rankings
[Keyword 1]: position [X]
[Keyword 2]: position [X]
[Keyword 3]: position [X]

### Domain Authority (optional)
DA (Moz) or DR (Ahrefs): [score]
```

---

## Monthly Report Template

Send this to the client every month. Keep it plain-language — they don't know what CLS is.

```
## Monthly Performance Report — [Month Year]
Site: [URL]

---

### Traffic
Organic visitors this month: [X] ([+/-]% vs last month)
Total visitors: [X]
Top traffic sources: [list]

### Search Rankings
[Keyword 1]: Position [X] → [X] ([improved/dropped/same])
[Keyword 2]: Position [X] → [X]
[Keyword 3]: Position [X] → [X]
New keywords entering top 20: [list]

### Conversions
Form submissions this month: [X] ([+/-]% vs last month)
Phone clicks: [X]
[Other goal]: [X]
Conversion rate on [key page]: [X]% (target: [X]%)

### What Improved
- [Plain-language win #1, e.g. "Contact form submissions up 23%"]
- [Win #2]

### What We're Testing Next
- [CRO experiment planned: e.g. "Testing a shorter contact form (3 fields vs 6)"]
- [SEO action: e.g. "Publishing FAQ page targeting 'how much does X cost' — 480 searches/mo"]

### Anything to Flag
- [Any drops, issues, or anomalies explained plainly]

---
Questions? Reply to this email or book a call: [link]
```

---

## CRO Experiment Log

Keep a running log of every experiment:

| Date | Page | Element Tested | Variant A | Variant B | Result | Winner | Implemented? |
|------|------|---------------|-----------|-----------|--------|--------|-------------|
| | | | | | | | |

**Before each experiment, document:**
- Hypothesis: "We believe [change] will [outcome] because [reason]"
- Primary metric: what we're measuring
- Sample size needed: minimum 100 conversions per variant for statistical significance
- Duration: minimum 2 weeks, ideally 4

---

## Rank Tracking Setup

Free options:
- **Google Search Console**: built-in, accurate, free. Position data under Performance → Queries.
- **Semrush** (free tier): 10 keywords tracked
- **Mangools** (paid but affordable): best UI for solo freelancers — ₹1,800/mo

Weekly check: note any keywords that dropped >5 positions. Investigate immediately.
Common causes: algorithm update, competitor published new content, technical issue (check Search Console → Index Coverage).

---

## Results-to-Retainer Conversion Phrases

Use these when presenting results to the client:

| Data point | Retainer pitch |
|------------|---------------|
| Traffic up 40% | "Organic is working. Let's amplify with Google Ads." |
| Contact form at 2% conversion | "Industry average is 4%. One A/B test could double your leads." |
| Ranking page 2 for main keyword | "We're one content piece away from page 1 — 480 searches/month at stake." |
| New keyword ranking appeared | "You're ranking for [keyword] without even targeting it. Let's build a page for it." |
| Bounce rate high on service page | "Users are leaving before reading the CTA. Let's test a layout change." |
| Phone clicks up 60% | "The site is driving calls. A CallRail setup would tell us exactly which keywords convert." |
