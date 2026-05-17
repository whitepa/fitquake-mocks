# Fitquake design mocks

Interactive design-decision rounds for Fitquake collaborator review.

**Live URL: https://whitepa.github.io/fitquake-mocks/**

## What's here

- `index.html` — landing page listing all open and past decision rounds
- `01-brand-and-shell.html` — Round 1: brand palette + logo, sidebar, card surface, avatars, trainer surface, member portal hero
- Future rounds will be added as `02-…html`, `03-…html`, etc., and linked from the index.

## For reviewers (Craig, Mike, …)

Open the live URL above. Click into the open round. Click your picks on each
dimension. Add a comment. Hit "Copy decision" at the bottom and paste the
string back to Phil.

Your selections are saved in your browser between visits.

## Workflow (for Phil)

To add a new decision round:

1. Create a new HTML file in this repo following the same skeleton as
   `01-brand-and-shell.html`. Key conventions:
   - Each `<section class="dimension" data-dim="N">` wraps one dimension.
   - Each option is `<label class="opt-wrap"><input type="radio" name="dimN" value="X">…</label>`.
   - Update `ROUND_ID` and `ROUND_TITLE` constants in the inline script.
   - Update `TOTAL_DIMS` to the number of dimensions in the round.
2. Add a new `<a href="0X-…html" class="decision-card">…</a>` entry to
   `index.html` under "Open rounds."
3. Commit and push — Pages rebuilds in ~30 seconds.

```bash
cd ~/src/fitquake-mocks
git add .
git commit -m "add: round 0X — <topic>"
git push
```

To close a round (mark it read-only and archived):

1. Change the badge in `index.html` from `<span class="badge open">Open</span>`
   to `<span class="badge closed">Closed</span>`.
2. Move it from "Open rounds" to a new "Closed rounds" section if you want
   to keep the index focused on what's actionable.
