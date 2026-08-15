# Contributing — your first PR

This site lives in a git repository, which means improving it *is* practice for improving robot code. Same branches, same pull requests, same review — just with words instead of Java, so the stakes are zero. That's on purpose: **your first pull request on this team should be to this site.**

## The ten-minute first PR

1. Find something to fix. A typo, a broken link, a **[FILL IN: …]** blank you know the answer to, or a tip from a workshop that isn't written down yet.
2. On the page, click the pencil icon (top right) — it takes you to the file on GitHub.
3. Click GitHub's pencil ("Edit this file"). Make your change right in the browser. The pages are plain Markdown; copy the formatting you see around you.
4. Scroll down → "Propose changes." GitHub creates a branch for you and opens a pull request form. Write one sentence about what you changed.
5. Someone reviews it (see below), you fix anything they flag, and it merges. The site rebuilds itself automatically within a couple of minutes.

That's the whole workflow the code team uses all season. You now know it.

## Who reviews

- Site changes: **[FILL IN: who has merge rights]**
- Robot code PRs get reviewed by **[FILL IN: code lead / mentor]**, and can also get an automated first pass from Claude — comment `@claude review` on the PR if it's set up on the repo. **[FILL IN: note whether the Claude GitHub app is installed, once decided]**

## House rules for this site

- **The [FILL IN: …] convention:** bold-bracketed blanks mark team-specific facts. Filling one in is a perfect first PR. Never delete one without replacing it with the real answer.
- Write like you talk. This site's voice is "helpful teammate," not "textbook."
- Short beats complete. A three-line answer that exists beats a perfect page that doesn't.
- If someone asks a question in Discord and the answer wasn't here — add it here after.
- The [style guide](style-guide.md) has the details: voice, formatting, and how exercises are written.

## Editing locally (optional)

For bigger changes, run the site on your laptop with live reload:

```bash
pip install mkdocs-material
mkdocs serve
```

Then open http://127.0.0.1:8000. See the repo README for details.
