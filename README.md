# Carrikcare Shift App (prototype)

A single-page prototype for Carrikcare, a healthcare staffing agency operating across Northern Ireland. It shows how shifts can be sent to workers, accepted, worked, signed off by the client home and invoiced, all from a phone or browser.

**Status:** demo prototype. All names, sites, locations and numbers are fictional. Nothing is saved after the page is reloaded, and there is no backend or login yet.

## Files in this repository

| File | Purpose |
|---|---|
| `index.html` | The whole app (HTML, CSS and JavaScript in one file) |
| `README.md` | This document |

## What it does

**Agency view**
- **Shifts:** create a shift and send it to a worker. Workers with expired or missing certificates cannot be selected. Quick send sends ready-made shifts (site, role, hours) for a chosen date in one tap, to the nearest free compliant worker.
- **Onboarding:** tracks four certificates per worker and flags those that are expired, expiring within 60 days or missing. Includes forms to onboard new workers and new clients (with client-specific rates).
- **Map:** schematic map of care sites and workers with distances, showing who is working today.
- **Insights:** weekly revenue and margin, a 14-day heatmap of who worked, and staff performance.
- **Invoices:** shows verified shifts ready to invoice, creates branded PDF invoices (logo, company details, VAT, payment terms), and downloads a per-shift authentication PDF or a CSV.

**Worker view**
- Review shift offers with distance, then accept or decline.
- Clock in and out. Each is accepted only within about 150 m of the site; otherwise it is rejected and logged.
- Home sign-off: the home representative enters their name, rates the worker on six criteria (matching the paper HCA timesheet), answers the concerns question and signs on screen.

Shift patterns used: Day 08:00-20:00, Morning 08:00-14:00, Afternoon 14:00-20:00, Night 20:00-08:00 and Night 20:00-10:00.

## Running it

Open `index.html` in a browser. No build step or install is needed. An internet connection is required because the page loads fonts (Google Fonts) and the PDF library (jsPDF, from cdnjs).

**Hosting with GitHub Pages:** go to Settings, then Pages, choose the main branch and the root folder, and save. The site is served over HTTPS, which browsers require for location access.

## Trying the full flow

1. Switch to **Worker** (top right) and choose "Daniel Reyes". Open the shift under New offers, review it and accept it.
2. Use **Clock in**. The "Location (demo)" selector lets you simulate being at the site or away from it. "Use my device location" will normally fail the check, because you are not at the site.
3. Use **Clock out**, then **Get home sign-off**. Fill in the representative's name, the ratings and a signature.
4. Switch to **Agency**, open **Invoices**, add your company details and logo, then tap **Create invoice**.

## Known limitations

- No persistence, backend, logins or roles. Data resets on reload.
- The map is a schematic drawing, not a live map. Workers and clients are placed by town, not street address.
- Invoice rates (Nurse 38, HCA 24) are placeholders. Per-client rates are used when a client is onboarded.
- Clock-in and clock-out times less than an hour apart bill the scheduled hours (a demo shortcut). Real shifts use the actual times, rounded to 15 minutes.
- Staff assessment ratings do not yet feed the performance charts.
- Company registration number, phone and email in the code were read from a scanned timesheet and must be checked. Address and bank details are blank.

## Roadmap to a production version

1. **Foundation:** database, user accounts, role-based access (agency, worker, home representative), two-step login for agency staff.
2. **Core flows:** push or SMS alerts for shift offers, server-side validation of location checks, stored signatures and audit log of every clock-in, sign-off and invoice.
3. **Pilot:** one or two homes and about 10 workers for 4 to 6 weeks, then fix and roll out.
4. **Later:** live maps and street-level addresses, accounting integration, rota and availability, performance scoring from assessments.

## Security and data protection

- Do not commit real worker, client or bank details to this repository.
- A production version should use encrypted storage, UK or EU hosting, automatic backups and an independent security test before go-live.
- Capture location only at clock-in and clock-out, and explain this in a privacy notice.
- Complete a data protection impact assessment, and register with the ICO as a data controller.
- Take legal advice on contracts and data protection before real use.
