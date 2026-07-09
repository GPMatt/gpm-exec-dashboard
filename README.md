# GPM Executive Dashboard

A tap-first dashboard for Marty, tuned for iPad Pro: a **four-card home page**,
each card a business area, each one a real page. Built as static,
dependency-free HTML — no build step, no backend, deployable straight to
GitHub Pages.

**Live preview:** enable GitHub Pages on this repo (Settings → Pages → branch
`main`, folder `/`) and the dashboard is served from the repo's Pages URL.

## Status: preliminary design, sample data only

Every number on every page is fictional placeholder data for design review.
**No real GPM tenant, property, or financial data is in this repo.**

## Structure

- **`index.html`** — home. Four cards: Property Management, My Investments,
  HR & Payroll, Billing. Tapping a card navigates to its page (a native
  cross-document view transition gives it a "zoom in" feel on browsers that
  support it — Safari/iPadOS 18+, Chrome — and falls back to a plain
  navigation elsewhere).
- **`property-management.html`** — the fully-designed view. Eight boxes
  (Financial Health, Revenue & Expenses, Portfolio Growth, Vacancy &
  Occupancy, Churn & Retention, Occupancy Forecast, Maintenance, Exception
  Alerts), each expanding in place into a full detail view on tap. This is the
  one page backed by real scoping work — see
  `GPM-Claude/Projects/P13_Dashboards/data_plan.md` (Layer 4 `calc_kpis` /
  Layer 5 `calc_weekly_snapshot`) for the eventual real data source.
- **`my-investments.html`**, **`hr-payroll.html`**, **`billing.html`** —
  placeholders. Each is a guess at what belongs on that page (a hero stat + a
  few tiles) so the visual direction is visible, not a scoped data model.
  Billing's numbers gesture at the already-live CC-receipt BillBack pipeline
  (project P12); HR & Payroll gestures at the maintenance-tech onboarding
  workflow (project PHR). Neither is wired to anything real yet.

## Design notes

- Distinct "executive" navy/slate theme, separate from the internal ops
  Command Center's brand palette — deliberately so Marty's view reads as its
  own thing.
- **Home → section is a page navigation** (tap a card, land on a new page,
  back link returns home). **Section → box detail stays expand-in-place**
  (tap a box on Property Management, it grows into an overlay on the same
  page; tap the backdrop or press Escape to zoom back out).
- iPad-oriented touch details: 44pt+ tap targets, `:active` press states
  instead of relying on `:hover`, safe-area padding for the top bar, and the
  `apple-mobile-web-app-capable` meta tags so it behaves reasonably if pinned
  to the home screen.
- Light and dark mode are both fully themed (auto-detects system preference,
  with a manual toggle in the top bar).
- Chart forms, color roles, and hover/tooltip behavior on the Property
  Management page follow this workspace's dataviz standard: sequential
  single-hue for magnitude, status colors (good/warning/serious/critical) for
  the delinquency aging bar, a legend + dash pattern (not a second hue) for
  actual-vs-projected occupancy.

## Open for feedback

This is v1 of the visual design. Next round should cover:
- Whether "Property Management" is the right name/home for what was
  originally "Business Analytics"
- What actually belongs on My Investments, HR & Payroll, and Billing — the
  current content on those three is a guess, not a spec
- Mobile/tablet layout on a real iPad Pro (currently responsive but only
  checked in a desktop browser at iPad-ish widths)
