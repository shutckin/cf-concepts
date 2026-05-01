# cf-concepts

Hosting for client video concept drafts. Each project lives at `docs/<8-char-uuid>/index.html` and is published via GitHub Pages.

URL pattern: `https://shutckin.github.io/cf-concepts/<uuid>/`

Used by the `content-pipeline` Claude Code skill — see `~/.claude/skills/content-pipeline/SKILL.md`.

## Add a new concept

```bash
cd ~/Documents/Claude/Projects/cf-concepts
UUID=$(uuidgen | tr '[:upper:]' '[:lower:]' | head -c 8)
mkdir -p docs/$UUID
cp /path/to/concept_doc/index.html docs/$UUID/
git add docs/$UUID
git commit -m "concept: <client> ($UUID)"
git push
echo "https://shutckin.github.io/cf-concepts/$UUID/"
```
