# Session 1 — Sketching

Sketches are where all the precision lives. A sloppy sketch makes every downstream feature fragile; a fully constrained sketch survives a whole season of edits.

- Create Sketch on a plane or a flat face. Draw with **Line (L)**, **Circle (C)**, **Rectangle (R)**, and arcs.
- **Dimension (D) everything.** Type exact numbers — never eyeball.
- **Constraints** lock geometry to intent: coincident, tangent, parallel, perpendicular, equal, midpoint, concentric. Use them instead of extra dimensions where you can.
- **Blue = still free. Black = locked down.** A finished sketch should be fully defined — all black. If it's blue, Fusion is choosing dimensions for you, and it will choose wrong at the worst time.
- Use **construction lines (X)** for symmetry axes and reference geometry, and anchor sketches to the **origin**.

Leaving sketches blue is the mistake everyone makes once. It works until the first edit, then everything downstream breaks.

<!-- TODO(phase 2): per SITE-BUILD-PLAN §6 — add one more constraint-practice exercise with a
     collapsible hint. Budget: 800 words. -->

!!! example "Exercise 1.1 — the fully defined sketch"

    Sketch a rectangular plate with a symmetric 4-hole pattern (pick real dimensions off any part in the shop). Fully define it: every line black, dimensioned off the origin.

    ??? tip "Stuck on the last blue lines?"

        Select a blue line and drag it — whatever moves is what's undefined. Usually it's a missing dimension to the origin, or a symmetry you meant to have but never told Fusion about (use a construction centerline + symmetry constraint).

!!! example "Exercise 1.2 — reverse-engineer a real part"

    Grab calipers (**[FILL IN: where the calipers live]**) and recreate one face of a real robot part as a sketch. Measured, dimensioned, black.
