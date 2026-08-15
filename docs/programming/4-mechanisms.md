# Level 4 — Mechanisms and sensors

## Motor modes

- `RUN_WITHOUT_ENCODER` — raw power. Fine for drivetrains in TeleOp.
- `RUN_USING_ENCODER` — the hub regulates velocity using encoder feedback. Smoother, consistent as battery sags.
- `RUN_TO_POSITION` — give it a target in ticks and a power; the hub drives there and holds. Perfect for lifts and arms:

```java
lift.setTargetPosition(1200);                  // ticks
lift.setMode(DcMotor.RunMode.RUN_TO_POSITION);
lift.setPower(0.8);                            // max effort toward target
```

Also set `setZeroPowerBehavior(BRAKE)` on mechanisms so they hold position at zero power instead of coasting.

## Servos

`servo.setPosition(0.0 to 1.0)` — it moves to that fraction of its range and holds. Continuous-rotation servos are different: setPosition maps to speed/direction, like a weak motor. Find positions with the servo tester: **[FILL IN: where the servo tester lives]**

## Sensors at a glance

| Sensor | What it gives you | Classic use |
| --- | --- | --- |
| Motor encoders | Ticks of rotation (built into FTC motors) | Distance driven, lift height |
| IMU (inside the Control Hub) | Robot heading (yaw) | Field-accurate turns in auto |
| Touch / magnetic limit switch | Pressed or not | Homing a lift, stopping at the ends |
| Distance sensor | Range to a surface | Detecting a game piece in the intake |
| Color sensor | Color + proximity | Sensing game elements or field tape |
| Webcam | Frames for vision processing | AprilTags, game-piece detection |

**Vision in one paragraph:** the SDK's VisionPortal has a built-in AprilTag processor — point a webcam at a tag and you get its ID and pose with almost no code. Season-specific game-piece detection builds on top of that. Our camera and vision setup: **[FILL IN: camera model + pipeline/library]**

!!! warning "Non-negotiable"

    Every mechanism gets software limits (encoder bounds or a limit switch) so a driver can't command it past physical travel. Broken string and stripped gears are a programming failure, not a driver failure.

<!-- TODO(phase 2): per SITE-BUILD-PLAN §6 — add a limit-switch homing exercise alongside 4.1.
     Budget: 1,100 words. -->

!!! example "Exercise 4.1"

    Add one mechanism to your TeleOp: two preset positions on buttons, RUN_TO_POSITION, software limits, current position on telemetry.

## Go deeper

<!-- TODO(phase 2): gm0 motors/servos/sensors pages; ftc-docs VisionPortal. -->
