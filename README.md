# Fitquake design mocks

Static HTML previews of Fitquake UI direction options. Live URL:
**https://whitepa.github.io/fitquake-mocks/**

## What's here

- `index.html` — current active mock (the design-options picker)
- Future iterations: `design-options-v2.html`, `dashboard-v1.html`, etc.

## For reviewers

Just open the live URL above. Each mock page explains how to give feedback.

## Workflow (for Phil)

To publish a new revision of the current picker:

```bash
cp /Users/whitepa/src/Fitquake2/fitquake2/docs/inspiration/design-options.html index.html
git commit -am "update: <what changed>"
git push
```

Pages rebuilds in ~30 seconds.

To add a new mock as a separate page (preserves the current one):

```bash
cp <source.html> mocks/<name>.html
# Update index.html to add a link to it
git add . && git commit -m "add: <name> mock" && git push
```
