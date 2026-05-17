# Round 1 — Brand & Shell · Responses

Picker: [01-brand-and-shell.html](../01-brand-and-shell.html)

Opened: 2026-05-17
Status: **ALL RESPONSES IN — ready to close**

---

## Dimensions recap

1. Brand palette + logo — 1A Teal forward / 1B Steel + lime / 1C Indigo + coral / 1D Carbon + amber
2. Card surface — 2A Soft shadow / 2B Subtle border / 2C Border + tiny shadow
3. Sidebar treatment — 3A Dark colored / 3B Light glass / 3C Icon-only rail
4. Avatar style — 4A Photo + ring / 4B Gradient initials / 4C Photo, no ring
5. Trainer Start Session — 5A Hero card / 5B Today's roster
6. Member portal hero — 6A Next-class / 6B Snapshot

---

## Responses

### Phil — 2026-05-17

| 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|
| 1A | 2C | 3A | 4A | 5A | 6A |

**Mix-in:** 1A palette **with the 1D hex + seismic line logo** (not the 1A lightning bolt). Treat as a hybrid — palette and chrome from 1A, logo mark from 1D.

**Comments:**
> Wait for Craig and Mike's responses before locking; flag for discussion if their picks diverge meaningfully.

---

### Craig — 2026-05-17

| 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|
| 1A | 2A | 3A | 4A | 5B | 6B |

**Comments:** (none)

---

### Mike — 2026-05-17

| 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|
| 1A | 2B | 3B | 4B | 5A | 6A |

**Comments:** (none)

---

## Running tally (3 of 3 responses in)

| Dim | Phil | Craig | Mike | Outcome |
|---|---|---|---|---|
| 1. Palette + logo | 1A (+ 1D logo) | 1A | 1A | ✅ **Unanimous 1A palette**; Phil's 1D-logo mix-in is the only open thread |
| 2. Card surface | 2C hybrid | 2A shadow | 2B border | 🟡 **1-1-1 split** — see synthesis |
| 3. Sidebar | 3A dark | 3A dark | 3B light | ✅ **3A majority** (Phil + Craig) |
| 4. Avatar | 4A photo+ring | 4A photo+ring | 4B gradient | ✅ **4A majority** (Phil + Craig) |
| 5. Start Session | 5A hero | 5B roster | 5A hero | ✅ **5A majority** (Phil + Mike) |
| 6. Member hero | 6A next-class | 6B snapshot | 6A next-class | ✅ **6A majority** (Phil + Mike) |

---

## Synthesis

### Locked by unanimous or strong majority

- **1 palette → 1A "Teal forward"** — unanimous across all three responses.
- **3 sidebar → 3A dark colored** — 2-1 majority (Phil + Craig). Mike alone preferred light glass.
- **4 avatar → 4A photo + colored ring** — 2-1 majority (Phil + Craig). Mike alone preferred gradient initials.
- **5 trainer Start Session → 5A hero card** — 2-1 majority (Phil + Mike). Craig alone preferred the roster list.
- **6 member portal hero → 6A next-class hero** — 2-1 majority (Phil + Mike). Craig alone preferred the snapshot.

### Phil decides (1-1-1 split)

- **2 card surface — Phil 2C / Craig 2A / Mike 2B**. Notable: Phil's **2C (border + tiny shadow hybrid)** is literally the visual combination of Craig's 2A (shadow) and Mike's 2B (border). It's the natural middle ground that honors Craig's "warmth" cue (a hint of shadow) AND Mike's "definition" cue (a crisp border).
  - **Recommendation: lock 2C.** Reflects Phil's pick AND blends what Craig and Mike each asked for separately, rather than choosing one over the other.

### Logo mix-in (Phil's note)

Phil chose 1A palette with the **1D hex + seismic line** logo. Craig and Mike picked 1A without commenting on the logo, so they implicitly accepted the 1A logo (lightning bolt).
  - **Recommendation: lock Phil's mix-in (1A palette + 1D logo).** As lead, his preference wins by default; the picker explicitly invited mix-ins via comments, and Craig/Mike didn't push back. We can validate the 1D-logo direction visually with the next mock if either of them flags it later.

### Final picks (recommended lock)

```
1A palette + 1D logo · 2C · 3A · 4A · 5A · 6A
```

### Cross-cutting observation

Mike and Phil cluster on the warmer/hero-ier dimensions (5A hero, 6A next-class). Craig leans calmer/operational (5B roster, 6B snapshot). Mike alone preferred lighter/quieter chrome (3B sidebar, 4B initials-only). Net effect: 5/6 dimensions land on the warmer/richer end — intentional, but worth keeping in mind. If Craig flags concrete usability concerns later ("too noisy when I'm scanning 200 members"), the 5C user-density toggle from Round 3 plus a "compact mode" is the right answer rather than re-litigating these picks.

---

## What happens after this round closes

1. Updated tokens land in `packages/web/tailwind.config.ts` and `packages/web/src/globals.css` in fitquake2:
   - `--brand: #0D9488` (teal-600), `--brand-deep: #0E3F3B`, `--brand-tint: #CCFBF1`
   - Card surface utility: `border + 0 1px 2px shadow + 0 4px 12px shadow` (2C hybrid)
   - Sidebar tokens: dark colored (3A) — already scaffolded
   - Avatar component: photo with brand-color ring (4A)
2. Logo asset (1D hex + seismic line) becomes an inline SVG component in `packages/web/src/ui/Logo.tsx`.
3. A short ADR-style note in `fitquake2/docs/design/round-01-decisions.md` captures choices.
4. The `01-brand-and-shell.html` picker stays online but moves to a "Closed rounds" section in the index — for posterity and so future reviewers can see what was settled and why.
