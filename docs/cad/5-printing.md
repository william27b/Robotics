# Session 5 — Design for 3D printing

- **Layers are the weak direction.** A printed part fails by peeling layers apart, so orient the part on the plate so loads run along layers, not across them. Design the part around how it will sit.
- **Overhangs past ~45° need support** — chamfer or bridge instead where you can. Chamfer bottom edges (fights elephant-foot and looks intentional).
- **Perimeters carry load, not infill.** Keep walls at least ~1.6 mm (two perimeters with a 0.4 mm nozzle); bump perimeter count before bumping infill on structural parts.
- **Printed threads are a trap.** Use heat-set inserts or captive nuts for anything you'll screw into more than once.

## Tolerances (starting points — calibrate to our printers)

| Fit | Clearance per side | Use it for |
| --- | --- | --- |
| Press fit | 0.0 – 0.1 mm | Bearings, pins, things that never come apart |
| Snug slip fit | 0.1 – 0.2 mm | Covers, lids, parts assembled by hand |
| Free / moving fit | 0.3 – 0.5 mm | Sliding parts, anything near a moving shaft |
| Holes in general | print undersized | Size up 0.2 – 0.4 mm or drill to final size |

Every printer/filament combo is different — print the team tolerance test coupon before trusting any number above. Printing a 6-hour part without ever printing the coupon is how you lose a Saturday. Our printers, filament, and slicer profiles: **[FILL IN: printer models, go-to filament, where tuned slicer profiles live, who approves long prints]**

**Exporting:** right-click the body → Save as Mesh → 3MF or STL, units mm. Name it like the part, not "export_final_v2 (3)".

<!-- TODO(phase 2): per SITE-BUILD-PLAN §6 — add an orientation worked example: one bracket, two
     orientations, which survives and why (describe it, don't render it). Budget: 1,100 words. -->

!!! example "Exercise 5.1 — tolerance coupon"

    Print the tolerance coupon on your assigned printer and record the results in **[FILL IN: where tolerance results are logged]**

!!! example "Exercise 5.2 — printable motor mount"

    Redesign your [2.1 motor mount](2-solids.md) as a printable part — orientation chosen for load, chamfered base, insert-ready holes — and print it. It should fit the motor on the first (fine, second) try.
