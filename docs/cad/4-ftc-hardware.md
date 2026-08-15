# Session 4 — Designing for FTC hardware

**Never model vendor parts from memory.** Pull real CAD and design around it:

- goBILDA and REV publish STEP files on nearly every product page — download and insert.
- Fusion has McMaster-Carr built in: Insert → **Insert McMaster-Carr Component**. Screws, bearings, and shafts drop straight into your design.
- GrabCAD and other community libraries cover most of the rest. Team parts library: **[FILL IN: link to the team's vendor CAD folder]**
- **Design on the ecosystem's grid.** Hole spacing, patterns, and shaft standards come from the vendor spec sheet — check it every time, don't guess from a photo. Our primary ecosystem and go-to dimensions: **[FILL IN: vendor + cheat-sheet link]**

Modeling a vendor part from a photo instead of its STEP file, and being 2 mm wrong, is a mistake that costs a print and a meeting.

## The sizing cube

Robots must **start each match inside an 18 × 18 × 18 inch cube** (expansion after start varies by season — the game manual is law). Keep a translucent 18-inch cube component in the robot assembly from day one and design inside it. Finding out at inspection is the expensive way.

## Master layout sketch

For the robot itself, work top-down: one layout sketch at the root of the assembly holds the big decisions — drivetrain footprint, wheel positions, mechanism reach arcs. Components reference it, so moving a line in the layout moves the whole design. This is how you change your mind cheaply in week 3.

## Iterate ugly, then detail

Block mechanisms out of primitive shapes first to answer the real questions — does it reach, does it fit, does it collide — and only detail geometry once the concept survives. CAD's whole job is making mistakes cheap. Detailing a mechanism before the layout sketch proves it fits and reaches is wasted evenings.

<!-- TODO(phase 2): per SITE-BUILD-PLAN §6 — Budget: 1,000 words. -->

!!! example "Exercise 4.1 — mini-assembly"

    Two inserted vendor parts + your [2.1 plate](2-solids.md), jointed together, sitting inside the sizing cube component.

## Go deeper

<!-- TODO(phase 2): gm0 design pages — the *why* behind mechanism and drivetrain choices. -->
