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

### Phil — 2026-05-17

| 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|
| 1D | 2C | 3B | 4A | 5B |

**Comments:**
> on 5B, I'm less concerned about the stated risk, as I think we should also support
> branding on the header for each business. i.e. an individual gym or trainer may
> have their own logo they'd like to display on the page when that business is activated.

---

### Craig — _awaiting response_

### Mike — _awaiting response_

---

## Follow-on implications from Phil's response

### Per-business header branding (from 5B comment)

Phil's comment introduces a new product capability we should scope explicitly: each
business can supply its own logo/brand color, which is displayed in the header (and
possibly the sidebar) whenever a user is operating in that business's context. This
serves two purposes — it mitigates the "which business am I in?" risk inherent to
the 5B header-dropdown approach, AND it's a real selling point for white-label /
multi-location operators.

**Legacy schema state:** the `businesses` table has no branding fields today
(`packages/api/src/db/schema/org.ts:24` confirmed — only `legalName`, `dba`,
`displayName`, `tz`, `businessType`, Stripe fields).

**Recommended fit:** use the existing file-storage pattern from Phase 6.5.G rather
than adding new columns. Attach a logo as a `BUSINESS_LOGO`-typed file via
`object_attachments`; the shell resolves "latest LOGO attachment for business N" at
load. Brand color could be a single new `brand_color` varchar column on
`businesses` (#hex), or a row in `object_info` per business. Either keeps the legacy
schema mostly untouched.

**Scope decision deferred to Round 3 or later:**
- Should brand color override our chosen palette tokens entirely, or just accent
  fields (header bar background, button color)?
- Logo aspect-ratio constraints (square vs. wordmark vs. both)?
- Fallback when no business logo uploaded (use Fitquake mark? hide entirely?)
- Free-tier limit (single logo) vs. premium (per-OU branding)?

These are bigger product-direction questions than fit in a Round 1/2 picker. Park
in `docs/PLAN.md` Phase 7-something or open a new "Per-business branding" round
once Phase 7a foundation is in.

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
