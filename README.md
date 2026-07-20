# Physician Freedom Calculators

Static calculator pages for the Physician Freedom System.

## Deploy

This project has no build step. Deploy the repository root as a static site.

Current pages:

- `index.html` - public/free Freedom Snapshot Calculator only, with paid-suite teaser cards.
- `tools-suite.html` - paid/member Tools Suite page with the paid Snapshot flow, M2 calculators, and the full M3 calculator suite.

Kajabi owns access control. The public opt-in page embeds `index.html`; the paid/member page should embed `tools-suite.html`.

## Review URLs

- Free Snapshot: `https://physicianfreedom-physician-freedom.vercel.app/index.html`
- Paid Tools Suite: `https://physicianfreedom-physician-freedom.vercel.app/tools-suite.html`
- Free QA route: `https://physicianfreedom-physician-freedom.vercel.app/index.html?review=1#qa`
- Paid QA route: `https://physicianfreedom-physician-freedom.vercel.app/tools-suite.html?review=1#qa`

The QA harness is hidden from normal paid users unless `?review=1`, `?qa=1`, or `#qa` is present.

## Paid Suite Sections

- Snapshot baseline: Paid Snapshot, Five-Minute Check, Freedom Delta / 300 Rule
- Cash & runway: Emergency Cash Target, Ninety-Day Stress Test, Off-Ramp Runway
- Disability protection: Disability Benefit Reality Check
- Retained income & tax: Retention Stack, Tax Reserve
- Investment cost: Fee Drag
- Real estate: Real Estate Cash Flow
- Contract scan: Contract Review / 7-Clause Scan
- Family access: Family Access Folder Checklist
- Action plan: Freedom System Scorecard, First Three Moves, Master Action Plan, Progress Tracker, Annual Review

## Milestone 4 Framework

- Summary report actions are available on both pages: open email draft, copy summary, and create a branded PDF-ready report.
- The PDF report opens as a styled report preview with a cover band, key metrics, interpretation text, and section results. The browser print dialog is used only as the local PDF renderer.
- Report summaries are generated locally from the current calculator state.
- Vendor-neutral analytics events are emitted through `window.dataLayer` and a `pfs:analytics` browser event.
- Kajabi iframe embedding is supported with `window.parent.postMessage({ type: "pfs:resize", ... })` height messages.

## Data Handling

All calculator math runs in the visitor's browser. User-entered financial numbers are not stored by these pages.
