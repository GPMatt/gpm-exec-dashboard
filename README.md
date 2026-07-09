# GPM Executive Dashboard

A tap-first dashboard for Marty, tuned for iPad Pro: a **six-card home page**,
each card a business area, each one a real page. Built as static,
dependency-free HTML — no build step, no backend, deployable straight to
GitHub Pages.

**Live preview:** enable GitHub Pages on this repo (Settings → Pages → branch
`main`, folder `/`) and the dashboard is served from the repo's Pages URL.

**This repo is public.** Anyone with the URL — including Marty — can view it
right now, unauthenticated. That's why every page carries a visible "Sample
data" chip.

## Status: preliminary design, sample data only

Every number on every page is fictional placeholder data for design review.
**No real GPM tenant, property, or financial data is in this repo.**

## Structure

- **`index.html`** — home. Six cards, minimal style (outlined box, centered
  title, no icon/description clutter): Management Metrics, Client
  Relationships, My Calendar, Business Analytics, Recent News, Inbox. Tapping
  a card navigates to its page (a native cross-document view transition
  gives it a "zoom in" feel on browsers that support it — Safari/iPadOS 18+,
  Chrome — and falls back to a plain navigation elsewhere).
- **`management-metrics.html`** — the fully-designed view (formerly
  "property-management.html" / originally "Business Analytics" in the very
  first draft). Eight boxes (Financial Health, Revenue & Expenses, Portfolio
  Growth, Vacancy & Occupancy, Churn & Retention, Occupancy Forecast,
  Maintenance, Exception Alerts), each expanding in place into a full detail
  view on tap. This is the one page backed by real scoping work — see
  `GPM-Claude/Projects/P13_Dashboards/data_plan.md` (Layer 4 `calc_kpis` /
  Layer 5 `calc_weekly_snapshot`) for the eventual real data source.
- **`my-calendar.html`** — placeholder with a sample agenda (today / tomorrow
  / Friday). Once connected, this pulls a live feed from Marty's calendar —
  not built, sample data only.
- **`my-email.html`** (card labeled "Inbox") — placeholder with a sample
  inbox (owner / legal / vendor / lender / tenant messages, tagged by
  category). Once his email is synced, this lists every business-relevant
  message in one place — not built, sample data only.
- **`client-relationships.html`**, **`business-analytics.html`**,
  **`recent-news.html`** — blank-slate placeholders, each with a short guess
  at what might belong there (owner relationship health for Client
  Relationships; strategic/growth metrics for Business Analytics; local
  market + industry headlines for Recent News) but no real spec yet.

## Not currently on the home page

- **`hr-payroll.html`** still exists with its original placeholder content
  but isn't linked from the six-card home grid (the new sketch only had room
  for six). Say the word if it should come back as a seventh card or replace
  one of the new ones.

## Design notes

- Distinct "executive" navy/slate theme, separate from the internal ops
  Command Center's brand palette — deliberately so Marty's view reads as its
  own thing.
- **Home cards are intentionally minimal**: an outlined box, a bold title in
  the accent color, and (for anything not yet scoped) a small "Coming soon —
  what do you want here?" line. No icons, stats, or affordance text — the
  whole card is the tap target.
- **Home → section is a page navigation** (tap a card, land on a new page,
  back link returns home). **Section → box detail stays expand-in-place**
  (tap a box on Management Metrics, it grows into an overlay on the same
  page; tap the backdrop or press Escape to zoom back out).
- iPad-oriented touch details: 44pt+ tap targets, `:active` press states
  instead of relying on `:hover`, safe-area padding for the top bar, and the
  `apple-mobile-web-app-capable` meta tags so it behaves reasonably if pinned
  to the home screen.
- Light and dark mode are both fully themed (auto-detects system preference,
  with a manual toggle in the top bar).
- Chart forms, color roles, and hover/tooltip behavior on the Management
  Metrics page follow this workspace's dataviz standard: sequential
  single-hue for magnitude, status colors (good/warning/serious/critical) for
  the delinquency aging bar, a legend + dash pattern (not a second hue) for
  actual-vs-projected occupancy.

## Open for feedback

This is v3 of the visual design. Next round should cover:
- Whether HR & Payroll should come back onto the home grid
- What actually belongs on Client Relationships, Business Analytics, and
  Recent News — each has a guess, none has a spec
- What "business relevant" means for Inbox once sync is scoped, and which
  calendar(s) feed My Calendar
- Mobile/tablet layout on a real iPad Pro (currently responsive but only
  checked in a desktop browser at iPad-ish widths)
