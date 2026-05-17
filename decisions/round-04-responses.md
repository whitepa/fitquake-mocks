# Round 4 — Persona-specific Dashboards · Responses

Picker: [04-persona-dashboards.html](../04-persona-dashboards.html)

Opened: 2026-05-17 (in response to Craig's persona-KPI feedback in Round 3)
Status: **ALL RESPONSES IN — ready to close**

---

## Why this round exists

Round 3 asked "what KPIs lead?" as if there were one universal answer. Craig (citing
ChatGPT-derived research) and Phil aligned on the insight that the right answer is
persona-dependent — a gym manager, a trainer, and a member each have different definitions
of "success." This round picks one KPI preset pack for each persona, which will seed the
default role templates that ship in Phase 7i (and the per-user widget placement layer from
Phase 6.5.H).

---

## Dimensions recap

1. Gym admin home (subscription gym manager) — 1A Growth (ChatGPT recommendation) / 1B Health / 1C Today
2. Trainer home (independent or staff trainer) — 2A Income (ChatGPT recommendation) / 2B Retention / 2C Today
3. Member portal home (gym member self-service) — 3A Activity / 3B Account / 3C Achievement

---

## Responses

### Phil — 2026-05-17

| 1 Gym admin | 2 Trainer | 3 Member portal |
|---|---|---|
| 1A Growth | 2C Today | 3A Activity |

**Comments:** (none)

---

### Mike — 2026-05-17

| 1 Gym admin | 2 Trainer | 3 Member portal |
|---|---|---|
| 1A Growth | 2C Today | 3C Achievement |

**Comments:** (none)

---

### Craig — 2026-05-17

| 1 Gym admin | 2 Trainer | 3 Member portal |
|---|---|---|
| 1A Growth | 2B Retention | 3A Activity |

**Comments:** (none)

---

## Running tally (3 of 3 responses in)

| Dim | Phil | Craig | Mike | Outcome |
|---|---|---|---|---|
| 1. Gym admin | 1A Growth | 1A Growth | 1A Growth | ✅ **Unanimous 1A Growth** (ChatGPT-aligned) |
| 2. Trainer | 2C Today | 2B Retention | 2C Today | ✅ **2C Today majority** (Phil + Mike) |
| 3. Member portal | 3A Activity | 3A Activity | 3C Achievement | ✅ **3A Activity majority** (Phil + Craig) |

---

## Synthesis

### Locked

- **Gym admin → 1A Growth (unanimous).** ChatGPT recommendation holds. Net member growth, churn, MRR, visits/member, revenue/member.
- **Trainer → 2C Today (majority Phil + Mike).** Sessions today, next session, earnings today, follow-ups, earnings MTD.
- **Member portal → 3A Activity (majority Phil + Craig).** Next class, visits this mo, PT remaining, monthly goal.

### Recommended lock

```
1A Growth (gym admin) · 2C Today (trainer) · 3A Activity (member)
```

### Notable findings

- **ChatGPT recommended 2A Income for trainers; no reviewer picked it.** All three landed on Today (2C) or Retention (2B). Both alternatives are operational/short-term rather than long-arc income. Likely reason: the fitquake trainer persona in practice is a staff trainer (back-to-back sessions, today-focused), not an independent practitioner running their own income book. **Recommendation: ship 2C as the staff-trainer default, AND offer 2A Income as a one-click switch in trainer settings for self-onboarded independents.** This adds nominal complexity (one extra role-template seed) but covers both modes.
- **Craig's 2B Retention pick is also worth honoring as an option** — even if not the default, "client lifetime + renewals due + no-show rate" is a meaningful trainer view for relationship-focused practitioners.
- **Member portal 3C Achievement (Mike's pick) requires backend work** we don't yet have (streak tracking, PR logging, goal-setting). 3A Activity uses metrics we can compute today.

### Backend implications

Per Round 4 What-Happens-After section: these picks seed the default role templates in
`packages/api/src/lib/dashboards/seeds.ts`. New work surfaces:

- **MRR computation** — sum of active subscription monthly equivalents. New aggregation; spec needed.
- **Churn % (windowed)** — cancellations / active members over rolling 30d. New aggregation.
- **Visits/member** — visits in period / active members. Computable from existing schedule_event_attendees.
- **Avg client lifetime** (relevant for 2B Retention if we ship it) — needs membership start/end window math.
- **PT remaining** (for member portal) — already computable from package + sessions used.

A short ADR will scope which need new compute work and land it in the Phase 7 plan.

_Will list:_
- Per-persona consensus (each persona gets one chosen KPI pack)
- Tensions worth surfacing (e.g., if reviewers want different defaults than what we expected)
- Any "swap one KPI" comments worth threading through implementation

---

## What happens after this round closes

1. The chosen KPI packs seed the default role templates in `packages/api/src/lib/dashboards/seeds.ts`
   (Phase 6.5.H delivered the schema + endpoints; this populates them).
2. Each persona's dashboard renders the corresponding KPI strip on first login. Users can
   still customize via the Phase 7i widget admin UI.
3. The metrics themselves become a backend implementation queue — some are already computable
   from existing schema (active members, MRR, visits/member), others may need new aggregations
   (avg client lifetime, churn % calculated as windowed metric, no-show rate). A short follow-on
   ADR will list which metrics need new compute work and where it lands in the Phase 7 plan.
