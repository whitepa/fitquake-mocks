# Round 4 — Persona-specific Dashboards · Responses

Picker: [04-persona-dashboards.html](../04-persona-dashboards.html)

Opened: 2026-05-17 (in response to Craig's persona-KPI feedback in Round 3)
Status: **OPEN** (collecting responses)

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

### Phil — _awaiting response_

### Craig — _awaiting response_

### Mike — _awaiting response_

---

## Synthesis (to be filled in once all responses are in)

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
