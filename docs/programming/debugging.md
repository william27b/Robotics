# Debugging playbook

The page you open mid-panic. In order of how often it happens:

| Symptom | First things to check |
| --- | --- |
| Crash on INIT: "Unable to find a hardware device with name …" | Config name vs code string — exact match, case-sensitive. Someone renamed one side. |
| OpMode isn't in the Driver Station list | Missing `@TeleOp`/`@Autonomous`, an `@Disabled` left on, or the deploy didn't actually happen — check the build output. |
| Robot doesn't move, no errors | Powers actually nonzero (telemetry them)? Robot battery on and charged? Motor wires seated? E-stop? |
| Drives backward / spins in circles | Direction reversal on the wrong side, or wires swapped between ports. Fix in code, not by re-wiring mid-panic. |
| Mechanism jitters or drifts at rest | ZeroPowerBehavior not set to BRAKE, or two commands fighting in the loop. |
| Controls feel laggy | Something blocking the loop — a `sleep()`, a long telemetry dump, or a while loop inside the main loop. |
| Random disconnects mid-run | Battery strap loose, wiring strain at the hub, WiFi congestion — bring in the build team, it's usually physical. |

**Golden rule:** telemetry first. Print the value you're assuming before debugging the logic that uses it.

Two habits that cost teams real matches: skipping telemetry and then debugging blind for an hour, and tuning on a dying battery and then wondering why everything is different in a match.

<!-- TODO(phase 2): per SITE-BUILD-PLAN §6 — add "how to read a stack trace on the Driver Station"
     and "when it's physical, not software". The table may grow rows freely (tables are exempt from
     the prose budget). Budget: 700 words of prose + table. -->
