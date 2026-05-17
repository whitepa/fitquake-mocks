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

### Phil — 2026-05-17 _(revised same day: Dim 1 1C → 1D)_

| 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|
| 1D | 2A | 3A | 4D | 5B | 6C |

**Comments:** (none)

> Original Dim 1 pick was 1C Activity-first; revised to 1D Mixed/balanced.

---

### Craig — _awaiting response_

### Mike — _awaiting response_

---

## Running tally (1 of 3 responses in)

Phil's picks lean balanced/operational — one KPI from each area (1D Mixed: Members, Revenue, Today's Sessions, Tasks, Alerts), full-width schedule grid (3A), mixed right rail (4D), compact density (5B), honest zeros for empty state (6C). The hero chart 2A revenue trend anchors the money narrative without forcing it into the KPI strip.

Notable pairing: **1D KPIs + 4D right rail** = both "small section from each area" pattern. Reduces redundancy concern between top-of-fold and right-rail (each shows different facets of the same areas: Tasks/Alerts shown as counts in 1D, as actionable items in 4D).

| Dim | Phil | Craig | Mike | Status |
|---|---|---|---|---|
| 1. KPI priority | 1D Mixed | — | — | awaiting |
| 2. Hero chart | 2A Revenue trend | — | — | awaiting |
| 3. Schedule placement | 3A Full-width grid | — | — | awaiting |
| 4. Right-rail | 4D Mixed | — | — | awaiting |
| 5. Density | 5B Compact | — | — | awaiting |
| 6. Empty state | 6C Minimal zeros | — | — | awaiting |

---

## Themes from feedback (not a response)

### Persona-specific KPIs (from Craig, 2026-05-17)

Craig surfaced a persona-driven insight — the dashboard's KPI strip (Round 3 Dim 1) and possibly its hero chart (Dim 2) and right-rail (Dim 4) should be **different by persona**, not picked once globally:

**For an individual trainer:**
- MRR (predictable income)
- Average client lifetime / retention
- Utilization %
- Revenue per client
- Active clients

**For a subscription gym (manager view):**
- Net membership growth (joins minus cancellations)
- Monthly churn %
- Visits per member (engagement / leading indicator of churn)
- MRR
- Revenue per member (PT, classes, retail)

If simplified to 3:
- **Trainer:** MRR · Avg client lifetime · Utilization %
- **Gym:** Net member growth · Churn % · Visits/member

Phil: agreed at high level — "the information presented needs to be geared towards the persona. An individual trainer needs different info than a gym manager."

### Implication for Round 3

- **Round 3 Dims 3, 5, 6 stay universal** — schedule placement, density, empty state are about layout/chrome, not persona-specific content.
- **Round 3 Dims 1, 2, 4 likely become persona-flavored** — KPIs, hero chart, right-rail content all vary by persona.
- **What's already locked from Round 3 doesn't need to be re-litigated.** Phil's 1D Mixed pick + 2A Revenue trend become reasonable "generic / fallback / new-tenant default" — what you see before you've picked a persona, or what shows on a multi-persona admin's home screen.
- **Round 4 (proposed) carries the persona-specific picks forward.** See proposal below.

---

## Proposed Round 4 — Persona-specific dashboards

Three personas, each gets its own KPI strip (and maybe hero chart + right rail). Pick from 2-3 preset packs per persona to keep the picker tight.

**Gym admin (subscription gym manager):**
- A: Growth (Net member growth, Churn %, MRR, Visits/member, Rev/member) — ChatGPT recommendation
- B: Health (Active members, MRR, PT utilization, 30d retention, 90d retention)
- C: Today (Check-ins today, Bookings, Cash today, Tasks due, Alerts)

**Trainer (individual or staff trainer):**
- A: Income (MRR, Rev/client, Sessions this month, Earnings MTD, Utilization)
- B: Retention (Active clients, Avg lifetime, No-show rate, Renewals due, Engagement)
- C: Today (Sessions today, Next session, Earnings today, Follow-ups due, Today's revenue)

**Member portal (gym member self-service):**
- A: Activity (Next class, Visits this month, Sessions remaining, Goal progress)
- B: Account (Membership, Next bill, Sessions remaining, Recent classes)
- C: Achievement (Streak days, Personal records, Visits goal, Class history)

Backend already supports per-role widget configuration via Phase 6.5.H (role templates +
per-user placement). Round 4 picks would seed the default role templates for the three personas.

This is a proposal — awaiting Phil's call to open Round 4 with this structure.

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
