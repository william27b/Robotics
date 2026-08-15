# Level 5 — Code that survives the season

The difference between week-2 code and week-12 code isn't cleverness, it's structure. Three habits:

## 1. One Robot class, thin OpModes

Hardware names, setup, and mechanism actions live in one class; OpModes just call it. Rename a motor in the config and you fix one line, not nine files.

```java
public class Robot {
    public DcMotor lift;
    public Servo   claw;

    public void init(HardwareMap hw) {
        lift = hw.get(DcMotor.class, "lift");
        claw = hw.get(Servo.class, "claw");
        lift.setZeroPowerBehavior(DcMotor.ZeroPowerBehavior.BRAKE);
    }

    public void openClaw()  { claw.setPosition(0.75); }
    public void closeClaw() { claw.setPosition(0.35); }
}
```

## 2. Constants in one place

Every tuned number — servo positions, lift heights, speeds — lives in one constants file. Tuning at competition means editing one screen, not grepping the codebase between matches.

## 3. State machines, not sleep()

In TeleOp, `sleep()` freezes the whole loop — including driving — while it waits. For multi-step actions ("raise lift, then open claw, then lower"), keep a state variable and advance it across loop passes: an enum + switch that checks "is this step done?" each pass. gm0's state-machine page has the full pattern; steal it. **[FILL IN: link to a team example, once one exists]**

Our house style — naming, packages, comments — lives in the [code conventions](../handbook/code-conventions.md) handbook page.

<!-- TODO(phase 2): per SITE-BUILD-PLAN §6 — add one short annotated enum+switch state machine
     example with a mermaid state diagram, and a "when NOT to abstract" section. Exercises:
     refactor your Level-3 TeleOp onto a Robot class; convert one sleep()-based sequence to a
     state machine. Budget: 1,200 words. -->

## Pitfalls

- Copying code you can't explain. Judges will ask you to walk through it — and so will the robot, at the worst time.
- One person who understands the codebase. Rotate who writes what; pair on anything scary. (This site exists because of exactly this failure mode.)

## Go deeper

<!-- TODO(phase 2): gm0 state machine page. -->
