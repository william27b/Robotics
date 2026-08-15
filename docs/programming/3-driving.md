# Level 3 — Driving for real (mecanum)

Most competitive FTC robots use mecanum wheels — the rollers let the robot strafe sideways. The standard mixing math, straight from Game Manual 0, replaces the loop body from [Level 2](2-first-opmode.md) (**reverse both right-side motors** for this to work):

```java
double y  = -gamepad1.left_stick_y;
double x  =  gamepad1.left_stick_x * 1.1; // tune: counters imperfect strafing
double rx =  gamepad1.right_stick_x;

// keep powers in [-1, 1] while preserving the ratio between wheels
double d = Math.max(Math.abs(y) + Math.abs(x) + Math.abs(rx), 1);

frontLeft.setPower((y + x + rx) / d);
backLeft.setPower((y - x + rx) / d);
frontRight.setPower((y - x - rx) / d);
backRight.setPower((y + x - rx) / d);
```

**Driver-feel upgrades** (small code, big scrimmage difference):

- **Deadband:** ignore stick values below ~0.05 so the robot doesn't creep from stick noise.
- **Input shaping:** squaring or cubing stick inputs (keeping the sign) gives fine control at low speed and full power at full deflection.
- **Slow mode:** hold a bumper to scale all powers by ~0.3 for lining up on game elements.

<!-- TODO(phase 2): per SITE-BUILD-PLAN §6 — give each driver-feel upgrade a short code fragment,
     add a "field-centric exists, here's the idea + link" paragraph (do NOT implement it here),
     and add a driver-feedback tuning exercise. Budget: 900 words. -->

!!! example "Exercise 3.1"

    Mecanum TeleOp with all three upgrades. Let a non-programmer test-drive it and tune to their feedback — that's the actual job.

    ??? tip "Hint: where does input shaping go?"

        Shape `y`, `x`, and `rx` *before* the denominator math, e.g. `y = Math.copySign(y * y, y);` — shaping after mixing distorts the wheel ratios and ruins strafing.

## Go deeper

<!-- TODO(phase 2): gm0 mecanum drive + field-centric pages. -->
