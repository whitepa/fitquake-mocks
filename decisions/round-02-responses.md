# Round 2 — Login & First Load · Responses

Picker: [02-login-and-first-load.html](../02-login-and-first-load.html)

Opened: 2026-05-17
Status: **OPEN** (collecting responses)

---

## Dimensions recap

1. Login page layout — 1A Split-screen / 1B Centered card / 1C Minimal / 1D Full-bleed
2. Loading / splash state — 2A Brand splash / 2B Minimal spinner / 2C Skeleton dashboard
3. Login error display — 3A Inline under field / 3B Banner above form / 3C Toast
4. "Forgot password" placement — 4A Small link under password / 4B Footer link / 4C Ghost button
5. Multi-tenant business switcher — 5A Pick at login / 5B Header dropdown / 5C Dedicated post-login

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
- Any cross-cutting comments worth threading through Phase 7a implementation

---

## What happens after this round closes

1. Decisions flow into the Phase 7a login + bootstrap implementation:
   - `packages/web/src/routes/(auth)/login.tsx` — adopts the chosen layout
   - `packages/web/src/routes/__root.tsx` — adopts the chosen loading/splash pattern
   - `packages/web/src/lib/errorDisplay.ts` — adopts the chosen error pattern
   - `packages/web/src/lib/businessContext.ts` — adopts the chosen switcher model
2. A short ADR-style note in `fitquake2/docs/design/round-02-decisions.md` captures choices.
3. The picker stays online, moves to "Closed rounds" in the index.
