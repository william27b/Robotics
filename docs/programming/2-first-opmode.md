# Level 2 — Your first OpMode

An **OpMode** is one runnable robot program; the Driver Station shows a list of them and you pick one per match. Here's a complete, working TeleOp — click the :material-plus-circle: markers for the guided tour:

```java
@TeleOp(name = "MyFirstTeleOp") // (1)!
public class MyFirstTeleOp extends LinearOpMode {
    @Override
    public void runOpMode() {
        // INIT: runs when you press INIT on the Driver Station
        DcMotor leftDrive  = hardwareMap.get(DcMotor.class, "left_drive"); // (2)!
        DcMotor rightDrive = hardwareMap.get(DcMotor.class, "right_drive");
        rightDrive.setDirection(DcMotor.Direction.REVERSE); // (3)!

        telemetry.addData("Status", "Initialized"); // (4)!
        telemetry.update();

        waitForStart(); // (5)!

        while (opModeIsActive()) {
            double drive = -gamepad1.left_stick_y; // (6)!
            double turn  =  gamepad1.right_stick_x;

            leftDrive.setPower(drive + turn);
            rightDrive.setPower(drive - turn);

            telemetry.addData("Left power", leftDrive.getPower());
            telemetry.update();
        }
    }
}
```

1. Registers this OpMode on the Driver Station list (autonomous programs use `@Autonomous`). No annotation, or `@Disabled` = it won't show up.
2. Fetches a device by its **configuration name** — the exact-string thing from [Level 1](1-robot-system.md).
3. One side is reversed because the motors physically face opposite directions; without it the robot spins in place.
4. Telemetry prints live values to the Driver Station — it's your printf, your debugger, and your tuning tool all season.
5. Blocks here until you press PLAY. Everything from here to the end of the while loop *is* the match.
6. Pushing a stick **up** reads as **negative** — everyone gets bitten by this once. The minus sign fixes it.

The loop runs many times per second; each pass reads sticks and sets powers.

<!-- TODO(phase 2): per SITE-BUILD-PLAN §6 — add the lifecycle section (init → waitForStart → loop),
     deploy-and-run steps, and a "reading telemetry" section. Add a "make a button print a message"
     micro-exercise and a collapsible hint per exercise. Budget: 1,000 words. -->

!!! example "Exercise 2.1"

    Deploy it, drive it. Then convert it to tank drive: left stick = left side, right stick = right side.

## Go deeper

<!-- TODO(phase 2): ftc-docs OpMode pages + the SDK's own sample OpModes. -->
