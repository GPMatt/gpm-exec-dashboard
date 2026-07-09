# GPM Executive Dashboard

A single-screen view for Marty: eight boxes, each one a business area, each one
zooms in for the detail. Built as a static, dependency-free HTML page — no
build step, no backend, deployable straight to GitHub Pages.

**Live preview:** enable GitHub Pages on this repo (Settings → Pages → branch
`main`, folder `/`) and the dashboard will be served from the repo's Pages URL.

## Status: preliminary design, sample data only

Every number on this page is fictional placeholder data for design review.
**No real GPM tenant, property, or financial data is in this repo.** Once the
visual design is signed off, the plan is to wire it up to the AppFolio data
pipeline described in `GPM-Claude/Projects/P13_Dashboards/data_plan.md`
(Layer 4 `calc_kpis` / Layer 5 `calc_weekly_snapshot`).

## The eight boxes

1. **Financial Health** — collection rate, total delinquency, aging buckets
2. **Revenue & Expenses** — units under management, maintenance cost as % of fee
3. **Portfolio Growth** — units added/removed, 6-month trend
4. **Vacancy & Occupancy** — occupancy rate, vacant 30+/45+ day counts
5. **Churn & Retention** — renewal rate, move-out velocity, MTM tenants
6. **Occupancy Forecast** — projected occupancy at 90 days / 6 months
7. **Maintenance** — open WOs, avg days to close, tech capacity
8. **Exception Alerts** — action list: 45+ day vacancies, 90+ day delinquents, 30+ day open WOs

## Design notes

- Distinct "executive" navy/slate theme, separate from the internal ops
  Command Center's brand palette — deliberately so Marty's view reads as its
  own thing.
- Click any box and it expands in place into a full detail view (no page
  navigation); click the backdrop or press Escape to zoom back out.
- Light and dark mode are both fully themed (auto-detects system preference,
  with a manual toggle in the top bar).
- Chart forms, color roles, and hover/tooltip behavior follow this workspace's
  dataviz standard: sequential single-hue for magnitude, status colors
  (good/warning/serious/critical) for the delinquency aging bar, a legend +
  dash pattern (not a second hue) for actual-vs-projected occupancy.

## Open for feedback

This is v1 of the visual design. Next round should cover:
- Whether the 8-box grouping matches how Marty actually thinks about the business
- Any metric that's missing or shouldn't be there
- Mobile/tablet layout (currently responsive but not yet tested on a real device)
