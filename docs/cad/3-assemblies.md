# Session 3 — Components, assemblies, and joints

**Bodies vs components, finally explained:** a body is dumb geometry. A component is a real part — it has its own origin, its own timeline, can move, and shows up in a bill of materials. Robots are assemblies of components. Hence [Rule #1](0-setup.md): new component *before* you model, and keep one part per component.

- **Insert parts you already have:** right-click a design in the data panel → Insert into Current Design. This links it — updates to the original flow into the assembly.
- **Ground the frame.** One component (usually the chassis) gets grounded; everything else positions relative to it.
- **Joints (J), not free-floating parts:** Rigid for bolted things, Revolute for wheels and arms, Slider for linear slides, Cylindrical for shafts that spin and slide. Use **As-Built Joint** when parts are already positioned.
- **Set joint limits, then drag the mechanism around.** This is free clearance-checking: drive an arm joint through its range and watch for collisions before anything is built.

Modeling before creating a component, then spending an evening untangling bodies, is the classic way to learn this lesson the slow way.

<!-- TODO(phase 2): per SITE-BUILD-PLAN §6 — add a joint-type chooser table and a
     common-joint-mistakes list. Budget: 900 words. -->

!!! example "Exercise 3.1 — make it spin"

    Assemble motor + your [2.1 mount](2-solids.md) + a wheel as three components. Rigid joint motor-to-mount, revolute joint on the wheel. Drag the wheel and watch it spin.
