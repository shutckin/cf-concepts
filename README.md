# cf-concepts

Hosting for client video concept drafts. Each project lives at `<8-char-uuid>/index.html` and is published via GitHub Pages.

URL pattern: `https://shutckin.github.io/cf-concepts/<uuid>/`

Used by the `content-pipeline` Claude Code skill — see `~/.claude/skills/content-pipeline/SKILL.md`.

## Auto-cleanup

A GitHub Action (`.github/workflows/cleanup.yml`) runs daily at 03:00 UTC and removes any concept folder where the first commit is older than **30 days**. This is a privacy/hygiene measure: published concepts auto-expire after a month.

To extend a specific concept's lifetime, re-publish it to a new UUID folder.

## Privacy guidelines

Concept HTML pages are public on the internet (URL is unguessable but not access-controlled). The `content-pipeline` skill enforces these rules at publish time:

- No prices, fees, or budgets
- No AI credit costs (Higgsfield, Kling, Veo, Seedance, Nano Banana, etc.)
- No internal time estimates in hours/days
- No technical model names that hint at production cost
- No internal client agreements

The published HTML contains only: creative idea, visual direction, storyboard, mood, sound, and the call-to-action button.

## Publishing a new concept (manual)

```bash
cd ~/Documents/Claude/Projects/cf-concepts
UUID=$(uuidgen | tr '[:upper:]' '[:lower:]' | head -c 8)
mkdir -p $UUID
cp /path/to/concept_doc/index.html $UUID/
git add $UUID
git commit -m "concept: <client> ($UUID)"
git push
echo "https://shutckin.github.io/cf-concepts/$UUID/"
```

## Manual cleanup trigger

```bash
gh workflow run cleanup.yml -R shutckin/cf-concepts
```
