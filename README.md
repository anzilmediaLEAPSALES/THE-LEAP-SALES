# SalesDesk by LEAP - B2B Sales Management Workbook (web app)

A free, single-page web app for small B2B sales teams: track companies, contacts, interactions,
opportunities, leads, account plans, weekly reviews, a 90-day plan and revenue - linked by IDs and
summarised on a live dashboard. Works on phone, tablet and desktop. Add / edit / remove everything.

**Live demo:** <your link here> - click "Try the demo" (no sign-up).

## Features
- 9 linked sheets (Companies, Contacts, Activities & Follow-ups, Opportunities, Leads, Account Planning,
  Weekly Review, 90-Day Plan, Transaction Ledger) with ~50 columns each, auto-calculated fields (ƒ)
  and editable dropdown lists
- Table / Cards / Kanban-board views, search, filters, column chooser, inline status editing, drag-and-drop stages
- Interactive dashboard: month selector, KPI cards with targets, click-through drill-downs, action centre
  (done / snooze), management alerts, donut / bar / trend charts, customizable widgets
- Settings: theme, accent colour, density, currency, targets & rules, stage probabilities, every dropdown list,
  per-sheet columns and ID prefixes
- Private accounts (email/password or Google) with real-time sync across devices; offline-tolerant
- Starts empty; optional fictional sample data

## Design
LEAP brand (charcoal #202020, bright orange #F07838, light greys, Montserrat). ERP-style UX inspired by modern
business suites: app-launcher home, collapsible sidebar, control panel with search + filters + group-by +
view switcher, clean underlined form fields, status pills. Fully responsive: bottom navigation, card lists and
full-screen forms on phones. Installable as an app (PWA: manifest, icons, service worker).
Logo files: public/logo-horizontal.svg, logo-horizontal-dark.svg, logo-icon.svg, favicon.svg, icon-*.png.

## Tech
Vanilla JavaScript + CSS in one HTML file (no build step) - Firebase Authentication, Cloud Firestore
(per-user documents, security rules), Firebase Hosting. SVG charts, HTML5 drag-and-drop.

## Architecture
- `users/{uid}/sheets/{sheet}` - one JSON document per sheet; `users/{uid}/meta/main` - lists, targets, settings
- `firestore.rules` restricts every read/write to the owner and validates the document shape
- Client keeps a local cache and debounced-pushes only changed sheets; snapshot listeners merge remote changes

## Deploy
See SETUP.md.

## Roadmap ideas
Per-sheet row-level storage for large datasets, team workspaces with roles, CSV import/export,
email verification, multi-language UI.

## Credit & licence
Designed from an Excel sales-management workbook. Add your preferred licence (e.g. MIT) before publishing.
