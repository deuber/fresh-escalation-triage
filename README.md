# fresh-escalation-triage

An interactive, single-page support engineering exercise. A grocery store writes in asking "Why did it tell us to order this?" about an order from a demand-forecasting system. You pick a ticket, check each layer that could be at fault, and call the root cause.

**Live page:** https://deuber.github.io/fresh-escalation-triage/

## What it shows

- **Four tickets, four root causes.** Each ticket's problem lives in exactly one layer:
  - **Data feeds:** a stale on-hand inventory feed makes the shelf look empty, so the system over-orders strawberries 4×.
  - **Item mapping:** a vendor sync changes the banana case size from 40 lb to 4 lb, so the order comes out 10× too large.
  - **Model forecast:** the model underestimates the Thanksgiving lift on sweet potatoes. Nothing is broken; it's a forecast miss.
  - **App logic:** delivery dates are calculated from a UTC timestamp, so late-afternoon approvals land a day late.
- **Check each layer:** sales, forecast and on-hand chart per ticket, plus the evidence table each check returns.
- **The SQL behind each check:** Databricks-style queries using CTEs, window functions and joins back to the source of truth.
- **Resolution for each ticket:** root cause, who fixes it, what I'd build so Tier 1 can catch it next time, and how I'd measure it.
- **Symptom to first check:** a quick triage table.
- **Things that trip people up:** stale feeds, duplicating joins, UTC vs. store time, and other common traps.
- **Is it worth automating?** A small calculator for escalations avoided and engineer hours saved.

## Honest scope

This is a **simulation**. Every store, item, number and table name is invented, and the page runs entirely in the browser with no network calls. It's a personal project modeled on the kinds of escalations described in public support engineering job postings for grocery AI platforms. Not affiliated with any company.

## Run locally

It's one static file with no build step:

```sh
open docs/index.html
# or
python3 -m http.server -d docs 8000
```

## Deploy

GitHub Pages → Settings → Pages → Source: `main` branch, `/docs` folder.
