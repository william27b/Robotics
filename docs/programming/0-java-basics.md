# Level 0 — Just enough Java

You need surprisingly little Java to read robot code. These five ideas cover 90% of what you'll see:

- **Variables and types:** `int` (whole numbers), `double` (decimals — motor powers live here), `boolean` (true/false), `String` (text). Example: `double power = 0.5;`
- **If / else:** do something only when a condition is true — "if the button is pressed, open the claw."
- **Loops:** `while` and `for` repeat code. All of TeleOp is one big while loop that runs until the match ends.
- **Methods:** named, reusable chunks of code that take inputs and can return a value. `openClaw()` beats pasting the same three lines everywhere.
- **Classes and objects:** a class is a blueprint; an object is a thing built from it. Robot code is objects (motors, servos, sensors) that you call methods on: `liftMotor.setPower(1.0);`

To actually absorb this, spend 2–4 hours on any free interactive Java course (W3Schools or Codecademy's Java track both work) — up through methods is plenty. Then come back; everything past this point is more fun than syntax drills.

<!-- TODO(phase 2): per SITE-BUILD-PLAN §6 — give each of the five ideas a one-line robot-flavored
     example, add a "when to stop" note, add a second exercise (a method with a conditional),
     and put a collapsible answer on each exercise. Budget: 800 words. -->

!!! example "Exercise 0.1"

    Write a method that takes a number of encoder ticks and returns distance in mm (make up the constants). If you can do that, you're ready.

## Go deeper

<!-- TODO(phase 2): any free Java course — it is not our job to be one. -->
