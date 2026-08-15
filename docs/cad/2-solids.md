# Session 2 — Sketch to solid

- **Extrude (E)** is 80% of FTC modeling. Watch the operation type: New Body vs Join vs Cut vs Intersect.
- **Press Pull (Q)** for quick face offsets; **Revolve** for round parts like spacers and hubs.
- The **Hole tool** beats sketched circles for fasteners: it knows standard clearance and tap sizes, so an M4 clearance hole is two clicks and always right.
- **Fillet / Chamfer late.** They're timeline features like everything else — adding them early makes later edits fail in confusing ways.
- **Patterns and Mirror** (rectangular, circular) instead of copy-pasting geometry. Change one instance, change them all.
- **Inspect → Measure (I)** and Section Analysis constantly. Trust measurements, not your eyes.

!!! note ""

    Don't model threads on printed parts — you'll tap the hole or use an insert ([Session 5](5-printing.md)), and modeled threads slow Fusion to a crawl.

<!-- TODO(phase 2): per SITE-BUILD-PLAN §6 — add a "which feature do I reach for" mini-table.
     Budget: 900 words. -->

!!! example "Exercise 2.1 — motor mount plate"

    Model a motor-mount plate from the spec sheet of **[FILL IN: the team's standard motor + product page link]**: pilot hole for the boss, bolt circle for the face screws, mounting holes to structure.

!!! example "Exercise 2.2 — lightening pattern"

    Add a rectangular pattern of lightening cuts to the plate, then change the plate size and watch the pattern update.
