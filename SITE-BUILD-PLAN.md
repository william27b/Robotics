# Team Learning Site — Build Plan

**Audience for this file: Claude Code (and human maintainers).** Read this whole file and the existing `docs/` content before writing anything. This plan is the contract for how the site grows.

---

## 1. What this is

An FTC team's learning site: crash courses (CAD + programming), team handbook, and onboarding, built so a recently graduated alum's knowledge survives their departure. It already exists as a working MkDocs Material scaffold — the job is to expand it into a complete, well-structured site, **not** to start over.

## 2. Mission and audience

- **Audience:** high schoolers, mixed experience (never-coded through FTC veterans), pre-season through competition.
- **Mission:** they have fun, they learn by doing, they can find resources fast, and the team never again depends on one person's head.
- **The site's moat is team-specific knowledge + a curated on-ramp.** Generic FTC depth already exists and is excellent (gm0.org, ftc-docs.firstinspires.org, CTRL ALT FTC). We link to it; we do not rewrite it.

## 3. Non-negotiable principles

1. **Depth budgets are hard caps.** Every page below has a word budget. If a topic wants more, that is the signal to add a "Go deeper" link to gm0/ftc-docs — not more words. A tight site that gets read beats a huge one that doesn't. Total v1 target: ~25 pages, roughly 25k words. Hundreds of pages is an explicit non-goal.
2. **Never invent technical facts.** No made-up SDK method names, part numbers, hole spacings, or dimensions. If unsure, write `<!-- TODO(verify): claim + authoritative source to check -->` and keep the claim out of the rendered text. Vendor dimensions come from spec sheets or become a `[FILL IN: …]`.
3. **The [FILL IN: …] convention.** Bold-bracketed blanks (`**[FILL IN: …]**`) mark team-specific facts only humans can supply (repo URLs, config names, printer profiles, who reviews what). Never fabricate these, never delete one without a real answer, and prefer creating one over guessing.
4. **Succession constraint.** Everything must be editable by a sophomore in the GitHub web editor: plain Markdown, no custom plugins, no build steps beyond `mkdocs-material`, no JavaScript beyond what the theme provides.
5. **Students do the work.** Pages teach patterns and give exercises; they never hand over complete season solutions. Old team code is *reference, not template* — say so wherever it's linked.
6. **Voice: helpful teammate, not textbook.** Second person, short sentences, honest about failure modes, occasional dry humor. Calibration lines from the existing pages: "get roasted, improve" · "Finding out at inspection is the expensive way." · "It worked at home" is not a version." Match that register.
7. **`mkdocs build --strict` must pass** on every change. Relative internal links only.

## 4. Existing scaffold (do not rebuild)

- `mkdocs.yml` — Material theme with `content.code.annotate`, `content.code.copy`, `content.tabs.link`, tabbed/details/tasklist/mermaid extensions configured. Keep as-is unless a page below requires a change.
- `docs/index.md` — front-page router (grid cards).
- `docs/cad.md`, `docs/code.md` — complete v0 crash courses. **These are the source of truth for voice and baseline content.** The build splits them into the per-page structure below, preserving their content and improving it within budget — not discarding it.
- `docs/contributing.md` — first-PR walkthrough.
- `.github/workflows/deploy.yml`, `README.md` — deploy pipeline; don't touch.

## 5. Target site map

```
Start here (index.md)                      — router, done-by-kickoff checklist
programming/
  index.md          — entry-point router + how this course works
  0-java-basics.md
  1-robot-system.md — how code reaches a robot; toolchain setup; configuration
  2-first-opmode.md
  3-driving.md      — tank → mecanum → driver feel
  4-mechanisms.md   — motor modes, servos, sensors, software limits
  5-architecture.md — robot class, constants, state machines
  6-autonomous.md   — encoders → IMU → path libraries
  debugging.md      — the playbook (symptom → checks)
  ladder.md         — practice ladder + how to get checked off
cad/
  index.md          — entry-point router + how this course works
  0-setup.md
  1-sketching.md
  2-solids.md
  3-assemblies.md   — components, joints
  4-ftc-hardware.md — vendor CAD, sizing cube, master layout sketch
  5-printing.md     — DFM, tolerances, exporting
  ladder.md
handbook/
  code-conventions.md
  cad-conventions.md
  the-repo.md       — annotated tour: structure is the lesson; template-repo + archive policy
  competition-day.md — code freeze, tagging, pit checklist, who does what
  resources.md      — curated links, one line each on *why*
contributing/
  first-pr.md       — (move of existing contributing.md)
  style-guide.md    — voice, Material syntax cheatsheet, FILL IN rule, exercise format
```

Update `nav:` in `mkdocs.yml` to match, with sections collapsed by default.

## 6. Page-by-page outlines

Format per page: **Purpose · Sections · Exercises · Interactive elements · Budget · Go-deeper links.**

### programming/index.md
- Purpose: route mixed levels to the right entry point; set the kickoff goal.
- Sections: the three on-ramps (from existing code.md intro); simulator callout (vrobotsim.com); what "done" means.
- Interactive: grid cards for the on-ramps.
- Budget: 400 words.

### programming/0-java-basics.md
- Purpose: minimum Java to read robot code; send them elsewhere to drill syntax.
- Sections: the five ideas (variables/types, if, loops, methods, classes-as-blueprints) each with a one-line robot-flavored example; where to practice (free courses, 2–4h, through methods); when to stop.
- Exercises: 0.1 ticks→mm method (existing); add one more tiny exercise (a method with a conditional).
- Interactive: collapsible "answer" on exercises.
- Budget: 800 words. Go deeper: any free Java course; not our job to be one.

### programming/1-robot-system.md
- Purpose: mental model of the hardware/software chain + working toolchain by the end.
- Sections: mermaid chain diagram (exists); Blocks/OnBot/Android Studio as tabs (exists); setup steps 1–4 with `[FILL IN]` deploy ritual; the configuration-names section (exists) — expand with one worked "rename a device end-to-end" example.
- Exercises: verify-your-setup checklist (task list) ending in a successful empty build.
- Budget: 1,000 words. Go deeper: ftc-docs hub/config pages.

### programming/2-first-opmode.md
- Purpose: first complete OpMode, understood line by line.
- Sections: annotated TeleOp (exists — keep the code annotations); lifecycle (init → waitForStart → loop); deploy-and-run steps; reading telemetry.
- Exercises: 2.1 tank conversion (exists); add "make a button print a message" micro-exercise.
- Interactive: code annotations mandatory; collapsible hint per exercise.
- Budget: 1,000 words.

### programming/3-driving.md
- Purpose: a robot drivers actually like.
- Sections: mecanum block with the gm0 mixing math (exists); deadband / input shaping / slow mode with a short code fragment each; a "field-centric exists, here's the idea + link" paragraph (do not implement it here).
- Exercises: 3.1 (exists, with hint); add a driver-feedback tuning exercise.
- Budget: 900 words. Go deeper: gm0 mecanum + field-centric pages.

### programming/4-mechanisms.md
- Purpose: move something that isn't a wheel, safely.
- Sections: motor modes incl. RUN_TO_POSITION snippet (exists); BRAKE; servos + CR servos; sensors table (exists); vision-in-one-paragraph (VisionPortal/AprilTag, `[FILL IN]` for team setup); software limits warning (exists).
- Exercises: 4.1 (exists); add a limit-switch homing exercise.
- Budget: 1,100 words.

### programming/5-architecture.md
- Purpose: code that survives 12 weeks and 5 authors.
- Sections: Robot class pattern with skeleton (exists); constants file; state machines vs sleep() — add a short annotated enum+switch example (one, small); when NOT to abstract.
- Exercises: refactor your Level-3 TeleOp onto a Robot class; convert one sleep()-based sequence to a state machine.
- Interactive: mermaid state diagram of the example state machine.
- Budget: 1,200 words. Go deeper: gm0 state machine page.

### programming/6-autonomous.md
- Purpose: crawl/walk/run path to a scoring auto.
- Sections: encoder driving (ticks math shown once); IMU turns; path libraries paragraph — Road Runner / Pedro Pathing with `[FILL IN: which we use + tuning doc]`; "start auto week 1" argument.
- Exercises: 6.1 out-turn-back ×3 (exists); add "park from two starting positions."
- Budget: 900 words. Go deeper: Learn Road Runner / Pedro docs.

### programming/debugging.md
- Purpose: the page you open mid-panic.
- Sections: symptom→checks table (exists) — may grow rows freely (tables exempt from prose budget); the telemetry-first golden rule; how to read a stack trace on the DS; when it's physical, not software.
- Budget: 700 words of prose + table.

### programming/ladder.md
- Purpose: self-paced proof of skill; the pre-kickoff bar.
- Sections: rungs 1–8 as task list (exists); what "checked off" means (`[FILL IN: who verifies]`); simulator note for rungs 1–4.
- Budget: 400 words.

### cad/index.md
- Purpose: route by experience; set the kickoff goal.
- Sections: from existing cad.md intro; session pacing note.
- Budget: 350 words.

### cad/0-setup.md — existing Session 0 + 60-second mental model + Rule #1 warning. Budget 600.
### cad/1-sketching.md — existing Session 1; add one more constraint-practice exercise with collapsible hint. Budget 800.
### cad/2-solids.md — existing Session 2; add a "which feature do I reach for" mini-table. Budget 900.
### cad/3-assemblies.md — existing Session 3; add a joint-type chooser table and a common-joint-mistakes list. Budget 900.
### cad/4-ftc-hardware.md — existing Session 4 (vendor CAD, McMaster insert, sizing cube, master layout sketch, iterate-ugly). Budget 1,000. Go deeper: gm0 design pages.
### cad/5-printing.md — existing Session 5 incl. tolerance table; add orientation worked example (one bracket, two orientations, which survives and why — describe, don't render). Budget 1,100.
### cad/ladder.md — existing ladder as task list + verification note. Budget 350.

### handbook/code-conventions.md
- Mostly `[FILL IN]` scaffolding: naming, packages, branch scheme, PR rules, comment expectations, tagging at competition. Write the structure and the *reasons*; leave specifics as blanks. Budget 500.

### handbook/cad-conventions.md
- Same treatment: file naming, hub folder structure, version milestones, review-before-print, sizing sign-off. Budget 500.

### handbook/the-repo.md
- Purpose: make the repository's *structure* teach, without making old code the template.
- Sections: annotated tour of the season-template layout (folders, Robot class location, constants, README); the policy — new season starts from the template, past seasons live in clearly labeled archive branches/repos ("reference, not template"); 2–3 "keep this pattern / we'd change this" callouts `[FILL IN: pick real examples with the maintainer]`.
- Budget: 800 words.

### handbook/competition-day.md
- Sections: code freeze + tag ritual; between-matches tuning rules (battery discipline); pit checklist (task list); roles `[FILL IN]`.
- Budget: 600 words.

### handbook/resources.md
- Curated list (exists across both courses — consolidate): gm0, ftc-docs, SDK samples, CTRL ALT FTC, Learn Road Runner/Pedro, FTC Discord, vrobotsim, vendor CAD sources, team archive `[FILL IN]`. One line each on *when to reach for it*. Budget 500.

### contributing/first-pr.md — move existing contributing.md; update links. 
### contributing/style-guide.md
- Sections: voice rules with the calibration lines from §3; Material syntax cheatsheet (admonition types we use and what each means: info=orientation, warning=safety/rules, example=exercise, tip=hint; tabs; annotations; task lists; mermaid); exercise format spec (title, body, optional one collapsible hint); the FILL IN rule; "add the Discord answer here after" rule. Budget 700.

## 7. Interactive toolkit — when to use what

- **Code annotations** (`// (1)!`): any code block over ~10 lines gets the annotated tour. Shorter fragments: plain.
- **Tabs:** only for genuine alternatives (tools, OS-specific steps). Never for sequence.
- **Collapsible (`??? tip`)**: hints and answers only — at most one per exercise. Never hide required content.
- **Admonitions:** semantic, per the style guide. Don't decorate.
- **Task lists:** ladders and checklists only.
- **Mermaid:** flows and state machines; keep under ~10 nodes.
- **Every course page ends with:** exercise(s), then "Go deeper" links.
- **Exercises must state where they're doable:** simulator, shop hardware, or laptop-only.

## 8. Working agreement (how Claude Code proceeds)

1. **Phase 1 — restructure:** create the tree in §5, move/split existing content into place, update `nav`, stub any page that lacks content with its §6 outline as visible TODOs. One PR. No new prose yet. `mkdocs build --strict` green.
2. **Phase 2 — draft:** write pages in batches of 2–3 per PR, in nav order, respecting budgets. Each PR description lists the pages, their word counts, and any `TODO(verify)` items introduced.
3. **Phase 3 — polish:** cross-links between courses and handbook, consistency pass against the style guide, kill orphan pages, final strict build.
4. Human maintainer reviews every PR (with Claude as second reviewer via `@claude review` where enabled). Do not self-merge. Do not resolve `[FILL IN]` blanks or check ladder boxes.
5. When existing text conflicts with this plan, the plan wins on *structure*, the existing text wins on *voice and facts*.

## 9. Backlog (v2+) — do not build in v1

- programming/vision.md (VisionPortal deep-ish dive, still link-heavy) · programming/control.md (PID intro → CTRL ALT FTC)
- cad/6-manufacturing.md (drawings, DXF, hand-fab tolerances)
- handbook/portfolio-and-judging.md (engineering portfolio structure, mock-judging how-to)
- handbook/outreach.md · Short embedded screen recordings for CAD sessions (placeholders OK in v1 as HTML comments)
- Per-mechanism cookbook pages — only if the team asks, and only as annotated *patterns*, never full season solutions.

## 10. Non-goals, stated once more

Rewriting gm0. Hundreds of pages. Custom theme work. JavaScript widgets. Complete season code. Anything a sophomore can't maintain from a browser.
