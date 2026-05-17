# Round 3 — Dashboard Layout & Widgets · Responses

Picker: [03-dashboard-layout.html](../03-dashboard-layout.html)

Opened: 2026-05-17
Status: **OPEN** (collecting responses)

---

## Dimensions recap

1. Information priority (KPI strip) — 1A Revenue-first / 1B People-first / 1C Activity-first / 1D Mixed
2. Hero visualization — 2A Revenue trend / 2B Visit trend / 2C Cash flow / 2D Member growth
3. Today's Schedule placement — 3A Full-width grid / 3B Side-rail list / 3C Hidden behind tab
4. Right-rail content — 4A Upcoming Schedule / 4B Tasks / 4C Alerts / 4D Mixed
5. Density — 5A Generous / 5B Compact / 5C User toggle
6. Empty / first-day state — 6A Illustrated / 6B Demo data with banner / 6C Minimal zeros

---

## Responses

### Phil — _awaiting response_

### Craig — _awaiting response_

### Mike — _awaiting response_

---

## Synthesis (to be filled in once all responses are in)

_Will list:_
- Where all reviewers agree (lock immediately)
- Where there's a 2-1 split (Phil decides or we discuss)
- Where there's a 1-1-1 split (we discuss)
- Cross-cutting tensions worth surfacing (e.g., 1A revenue-first KPIs + 5A generous density implies a different "tone" than 1C activity-first + 5B compact)

---

## What happens after this round closes

1. Drives the Phase 7a dashboard placeholder → real layout. The actual dashboard ships in 7i with
   widget customization, but 7a needs an opinionated default to render once the user lands post-login.
2. Locks the KPI ordering for the default dashboard role template (admin role gets these 5 KPIs first).
3. Sets the spacing scale in `packages/web/tailwind.config.ts` for the entire app.
4. Empty-state choice flows into every "no data yet" surface in the app (members list, transactions
   list, schedule, etc.) — sets a consistent first-run aesthetic.
