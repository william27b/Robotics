# Team docs site

*This is a test website; its design was aided by Claude Code.*

Crash courses and team knowledge, built with [MkDocs Material](https://squidfunk.github.io/mkdocs-material/). Content is plain Markdown in `docs/` — anyone on the team can edit it from the GitHub web editor.

## Preview locally

```bash
pip install mkdocs-material
mkdocs serve          # live-reloading preview at http://127.0.0.1:8000
```

Needs Python 3.9 or newer. If `pip install` fails, check `python3 --version` — an old
system Python is the usual cause. `mkdocs build --strict` must pass before you push.

## Publish

Live at <https://william27b.github.io/Robotics/>. The GitHub Action in
`.github/workflows/deploy.yml` rebuilds and publishes on every push to `main`.

**One-time setup, if Pages isn't on yet:** repo Settings -> Pages -> Source:
"Deploy from a branch" -> Branch: `gh-pages`. The branch appears after the Action
runs for the first time.

## Before going live

Search the project for `FILL IN` and replace each blank — or leave some for students to fill via their first PRs (see the Contributing page).

## Structure

- `mkdocs.yml` — site config, theme, navigation
- `docs/index.md` — front page / router
- `docs/programming/` — programming crash course (levels 0–6, debugging playbook, practice ladder)
- `docs/cad/` — CAD crash course (sessions 0–5, practice ladder)
- `docs/handbook/` — team conventions, the repo tour, competition day, resources
- `docs/contributing/` — the first-PR walkthrough and the style guide
