# Round 2 — Login & First Load · Responses

Picker: [02-login-and-first-load.html](../02-login-and-first-load.html)

Opened: 2026-05-17
Status: **ALL RESPONSES IN — ready to close**

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

### Craig — 2026-05-17

| 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|
| 1D | 2B | 3A | 4B | 5B |

**Comments:** (none)

---

### Mike — 2026-05-17

| 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|
| 1D | 2C | 3B | 4B | 5B |

**Comments:** (none)

---

## Running tally (3 of 3 responses in)

| Dim | Phil | Craig | Mike | Outcome |
|---|---|---|---|---|
| 1. Login layout | 1D Full-bleed | 1D Full-bleed | 1D Full-bleed | ✅ **Unanimous 1D** |
| 2. Loading state | 2C Skeleton | 2B Minimal spinner | 2C Skeleton | ✅ **2C majority** (Phil + Mike) |
| 3. Error display | 3B Banner | 3A Inline | 3B Banner | ✅ **3B majority** (Phil + Mike) |
| 4. Forgot password | 4A Small link | 4B Footer | 4B Footer | ⚠️ **4B majority** (Craig + Mike) — Phil is the outlier |
| 5. Business switcher | 5B Header dropdown | 5B Header dropdown | 5B Header dropdown | ✅ **Unanimous 5B** |

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

## Synthesis

### Locked by unanimous or strong majority

- **1 login layout → 1D Full-bleed brand** — unanimous. The bold-immersive option won everyone. Pairs naturally with Round 1's locked teal palette.
- **2 loading state → 2C Skeleton dashboard** — 2-1 majority (Phil + Mike). Craig preferred the minimal spinner. The skeleton has best perceived performance and "feels modern"; Craig's preference is also defensible (less code to maintain) but the majority wins.
- **3 error display → 3B Banner above form** — 2-1 majority (Phil + Mike). Craig preferred inline-under-field. Banner trades precision for security-mindedness ("don't tell attackers which field was wrong"); fine for login but we should still use 3A inline-under-field for non-security forms throughout the app where precision matters more.
- **5 business switcher → 5B Header dropdown** — unanimous. Plus Phil's per-business branding follow-on (already parked as Phase 7j in `docs/PLAN.md`) addresses the only real risk of header-dropdown switching.

### Majority goes against Phil (2-1)

- **4 forgot password → 4B Footer link below form** — Craig + Mike align. Phil picked 4A (small link under password). The 4B "Trouble signing in? Reset password" framing also covers things beyond just password (account locked, contact admin) — Mike+Craig's preference probably reflects that.
  - **Recommendation: lock 4B per majority.** Phil's 4A is also fine, but 4B is more flexible and the majority calls it. Low-stakes UX — easy to revisit.

### Final picks (recommended lock)

```
1D · 2C · 3B · 4B · 5B
```

### Follow-on (already parked)

Phase 7j — per-business header branding — covers the visible-business-context concern from 5B. See `docs/PLAN.md`. No further action needed in Round 2 closure.

---

---

## What happens after this round closes

1. Decisions flow into the Phase 7a login + bootstrap implementation:
   - `packages/web/src/routes/(auth)/login.tsx` — adopts the chosen layout
   - `packages/web/src/routes/__root.tsx` — adopts the chosen loading/splash pattern
   - `packages/web/src/lib/errorDisplay.ts` — adopts the chosen error pattern
   - `packages/web/src/lib/businessContext.ts` — adopts the chosen switcher model
2. A short ADR-style note in `fitquake2/docs/design/round-02-decisions.md` captures choices.
3. The picker stays online, moves to "Closed rounds" in the index.
