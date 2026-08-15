# Level 6 — Autonomous

Auto is worth disproportionate points every season, and it's pure programming. Build it in stages:

- **Crawl — encoder driving:** convert distance to ticks (ticks-per-rev and wheel circumference from the spec sheets), RUN_TO_POSITION on all four wheels. Gets you "drive 24 inches, turn, park."
- **Walk — IMU turns:** read heading from the hub's IMU and turn until you hit the target angle. Encoder turns drift; IMU turns don't.
- **Run — a path-following library:** Road Runner and Pedro Pathing both drive smooth, repeatable field paths using odometry, with real tuning docs. What we use, and our tuning notes: **[FILL IN: library + team tuning doc]**

Treating auto as a week-8 project is how teams end up with no auto. Start it week 1; even a reliable park scores.

<!-- TODO(phase 2): per SITE-BUILD-PLAN §6 — show the ticks math once, expand the path-library
     paragraph, make the "start auto week 1" argument properly, and add a "park from two starting
     positions" exercise. Budget: 900 words. -->

!!! example "Exercise 6.1"

    Encoder auto: drive forward a set distance, IMU-turn 90°, drive back. Repeatable three times in a row before you call it done.

## Go deeper

<!-- TODO(phase 2): Learn Road Runner / Pedro Pathing docs. -->
