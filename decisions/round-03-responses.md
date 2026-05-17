# Round 3 — Dashboard Layout & Widgets · Responses

Picker: [03-dashboard-layout.html](../03-dashboard-layout.html)

Opened: 2026-05-17
Status: **ALL RESPONSES IN — ready to close**

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

### Craig — 2026-05-17

| 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|
| 1A | 2D | 3B | 4D | 5C | 6A |

**Comments:** (none)

---

### Mike — 2026-05-17

| 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|
| 1D | 2B | 3B | 4A | 5A | 6B |

**Comments:** (none)

---

## Running tally (3 of 3 responses in)

| Dim | Phil | Craig | Mike | Outcome |
|---|---|---|---|---|
| 1. KPI priority | 1D Mixed | 1A Revenue | 1D Mixed | ✅ **1D majority** (Phil + Mike) — but superseded by Round 4 per-persona picks |
| 2. Hero chart | 2A Revenue | 2D Member growth | 2B Visit trend | 🟡 **1-1-1 split** — see synthesis |
| 3. Schedule placement | 3A Full-width | 3B Side-rail | 3B Side-rail | ⚠️ **3B majority** (Craig + Mike) — Phil is the outlier |
| 4. Right-rail | 4D Mixed | 4D Mixed | 4A Upcoming | ✅ **4D majority** (Phil + Craig) |
| 5. Density | 5B Compact | 5C User toggle | 5A Generous | 🟢 **1-1-1 split — but 5C compromise option exists** |
| 6. Empty state | 6C Minimal | 6A Illustrated | 6B Demo | 🟡 **1-1-1 split** — see synthesis |

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

## Synthesis

### Locked or settled

- **3 schedule placement → 3B Side-rail list** — 2-1 majority (Craig + Mike). Phil's 3A full-width is the outlier here. Worth noting: the inspiration screenshot used full-width; Craig and Mike both pulled toward saving vertical space. **Recommendation: lock 3B.** The schedule grid still exists as a first-class Calendar page (Phase 7d); the dashboard rail just shows next 5-6 sessions.

- **5 density → 5C User toggle** — pure 1-1-1 split (Phil 5B compact / Craig 5C toggle / Mike 5A generous), but **5C is the only option that satisfies all three reviewers** by letting each user pick their own. This is exactly the use case 5C was designed for. **Recommendation: lock 5C with "Comfortable" as the default**, so the out-of-box experience is closest to Mike's preference (and the inspiration); power users like Phil can switch to Compact in their prefs.

- **4 right-rail → 4D Mixed** — 2-1 majority (Phil + Craig). Will likely be overridden per-persona later, but as a generic default 4D works (small section of Upcoming, Tasks, Alerts).

### Superseded by Round 4

- **1 KPI priority** — 2-1 for 1D Mixed (Phil + Mike). Useful as the "default / no-persona / fallback" pick; Round 4's per-persona packs take over for the actual rendering.

### Phil decides (genuine 1-1-1 splits)

- **2 hero chart — Phil 2A Revenue / Craig 2D Member growth / Mike 2B Visit trend**. Three completely different preferences, no natural compromise. Each chart implies a different business narrative (money / growth / activity).
  - **Two paths:**
    - **(a) Phil picks one** as the generic default (his 2A revenue trend is reasonable; matches the inspiration), AND we open a future round for per-persona hero charts (admin = revenue, trainer = utilization, member = no chart).
    - **(b) Defer entirely**, pick per persona in a later round, leave the dashboard chart-less in the generic fallback.
  - **Recommendation: (a) — lock 2A as generic default + plan for per-persona overrides** in a future round once Round 4 closes.

- **6 empty state — Phil 6C Minimal zeros / Craig 6A Illustrated / Mike 6B Demo data**. Each picked a different option. No compromise option.
  - **Recommendation: lock Phil's 6C Minimal zeros.** As lead pick, plus 6C is the safest of the three (honest, no risk of "what is this data?" confusion that 6B carries, no extra illustration work that 6A needs). 6A and 6B can be revisited if we get user feedback that the empty state feels too sparse.

### Final picks (recommended lock)

```
Generic dashboard (when persona unknown):
  1D Mixed (fallback) · 2A Revenue trend · 3B Side-rail schedule · 4D Mixed rail · 5C User toggle (default Comfortable) · 6C Minimal zeros

Per-persona overrides for Dims 1 (and likely 2/4 later): see Round 4.
```

### Cross-cutting observation

Mike landed alone on 3 of 6 dimensions (3B align with Craig but disagreed elsewhere — 5A density, 6B empty state). He consistently picks the "warmer / more illustrated / more space" options, while Phil picks the "tighter / more honest / power-user" ones. Craig falls between them. The 5C user-toggle outcome lets all three live with the result, which is the right call when the underlying preferences are genuinely personal.

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
