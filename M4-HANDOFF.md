# Physician Freedom Tools Suite - Milestone 4 Handoff

Prepared for Umar Tariq.

## Current Live Pages

- Free Snapshot: https://physicianfreedom-physician-freedom.vercel.app/index.html
- Paid Tools Suite: https://physicianfreedom-physician-freedom.vercel.app/tools-suite.html
- Free QA route: https://physicianfreedom-physician-freedom.vercel.app/index.html?review=1#qa
- Paid QA route: https://physicianfreedom-physician-freedom.vercel.app/tools-suite.html?review=1#qa

## Product Structure

The public page remains focused on the free Freedom Snapshot Calculator only. Paid calculators are not embedded under the free Snapshot. The paid Tools Suite page contains the paid Snapshot flow plus the current Founding Edition calculators.

Kajabi owns access control. The public Kajabi opt-in page should embed or link to `index.html`. The paid/member Kajabi page should embed or link to `tools-suite.html`.

## Paid Tools Suite Navigation

The paid suite opens with an input-family overview. Each section groups calculators by shared inputs or evidence so users do not have to scroll through unrelated tools.

- Snapshot baseline: Paid Snapshot, Five-Minute Check, Freedom Delta / 300 Rule
- Cash & runway: Emergency Cash Target, Ninety-Day Stress Test, Off-Ramp Runway
- Disability protection: Disability Benefit Reality Check
- Retained income & tax: Retention Stack, Tax Reserve
- Investment cost: Fee Drag
- Real estate: Real Estate Cash Flow
- Contract scan: Contract Review / 7-Clause Scan
- Family access: Family Access Folder Checklist
- Action plan: Freedom System Scorecard, First Three Moves, Master Action Plan, Progress Tracker, Annual Review

## Summary Report Framework

Both pages now include a browser-side summary report framework:

- Open email draft
- Copy summary
- Print / save PDF

The summary is generated locally from the current calculator state. No automatic backend email service is connected yet. This keeps the current implementation credential-free while giving Kajabi, email automation, or CRM tooling a clear integration point later.

## Analytics Event Framework

Both pages emit vendor-neutral analytics events:

- `calculator_view`
- `report_email_draft`
- `report_copy`
- `report_print`

Events are pushed to `window.dataLayer` when available and are also emitted as a `pfs:analytics` browser event. This allows Google Tag Manager or another analytics layer to listen without changing calculator formulas.

## Kajabi Embed Support

Both pages post iframe resize messages to the parent page:

`{ type: "pfs:resize", page, section, height }`

Kajabi can ignore these safely. If a future Kajabi Custom Code wrapper wants dynamic iframe height, it can listen for `pfs:resize` and update the iframe height.

## QA Status

Current review-mode QA:

- Free Snapshot: all 25 checks passing
- Paid Tools Suite: all 289 checks passing

Desktop and mobile were checked after the latest section navigation, summary panel, and layout refinements. Review/admin QA is hidden from normal users unless the URL includes `?review=1`, `?qa=1`, or `#qa`.

## Remaining Integration Options

The following can be connected when credentials or platform decisions are available:

- Replace mailto email draft with Kajabi form/API, Zapier, Make, or another email automation.
- Connect analytics events to GTM, GA4, Kajabi analytics, PostHog, or another tracking layer.
- Add server-side PDF generation if automatic attached PDFs are required instead of browser print/save.
- Move the paid page into a Kajabi product/member area or offer once the final access structure is confirmed.
