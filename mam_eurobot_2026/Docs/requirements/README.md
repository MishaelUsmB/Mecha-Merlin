# System Requirements — SINJAB (Eurobot 2027)

This page records project requirements derived from the **Eurobot and Eurobot Junior 2027 Rules, Official 1.0**. The official document is supplemented by the separate general rules, and the organizers may issue clarifications during the year. Recheck both before treating a value or interpretation here as final.

## 1) Playing Area
- Playing surface: **3000 × 2000 mm**, with **70 mm** height and **22 mm** thick outer borders.
- Each team's throne room is a **500 × 500 mm** start and finish area. The marked line and adjacent table border are included.
- The field contains castle courtyards, ramparts, moats, SIMA stables, and stone quarries. Use the official appendix for their exact positions, colors, and materials.

## 2) Game Elements
- **30 stones:** cardboard boxes measuring **320 × 110 × 110 mm**. Each has an ArUco tag with value **13** on each of its four large faces. The quarries contain three horizontally oriented stones stacked vertically.
- The rules specify the stone tag value, but not its dictionary or physical marker size; verify both on the official elements before using camera pose estimates for manipulation.
- **Ramparts:** walls use a **200 × 400 mm** rectangular area; towers use a **200 mm** diameter circular area. A wall is three horizontal stones stacked; a tower is one vertical stone; a gate is two vertical stones topped by one horizontal stone (called a “door” in the points table).
- **Grail:** team-built, larger than a **60 mm** cube; it starts on the team's throne-room floor and must be raised within the castle.
- **SIMAs (knights):** team-built mobile actuators that start in the designated stable areas.
- **Cannonballs:** each team has **10** compressible foam balls, **45 mm** in diameter.

## 3) Actions and Scoring
- **Build Camelot:** 1 point per stone in a construction zone; 5 per wall; 5 per tower; 20 per gate.
- **Raise the Grail:** 5 points for a Grail in the castle, plus 5 per elevation level.
- **Return the King:** 5 points for the main robot partially in its own throne room at match end, or 10 points if fully inside.
- **Attack (optional):** the attack phase runs from the **85th second** to match end. SIMAs may occupy the opposing moats or attack opposing SIMAs; robots/SIMAs may send cannonballs into the opposing castle. Scoring includes 5 points per opposing moat occupied, 5 for a SIMA attack, 5 if at least one cannonball is in the opposing courtyard, and 15 additional points if at least three are there.
- Actions are independent; no single action is mandatory. Favor simple, reliable mechanisms and strategies.

## 4) Implementation Scope
- Update perception and manipulation from colored crates to the 2027 stones, including recognition of the official tag value.
- Model the 2027 field and its elements in simulation using the official appendix layout rather than the 2026 mat and crate placements.
- Add mission support for construction and Grail placement, then returning the main robot to its throne room.
- Treat the attack phase as an optional extension; do not activate attack actions before 85 seconds.
- Keep the simulation and controller configurable for team side/color and verify against the latest official clarifications.

**Current repository status:** the ArUco detector recognizes the 2027 stone marker ID and the controller can target stones, but its grab state is a placeholder. Marker dictionary and size remain provisional. The `mam_eurobot_2026` arena and crate models remain 2026 prototypes; construction, Grail handling, return-zone logic, and scoring are still pending.

## 5) Mechanical and Software Interfaces
- Check robot, SIMA, Grail, and safety limits against the current separate general rules before design release; this rules document alone does not provide all envelope constraints.
- Preserve interfaces for camera/perception, navigation, manipulation, and game logic so stones, construction zones, and the throne room can be represented consistently.
- Keep the simulation-first workflow and record match-end scoring-relevant state.

## 6) Verification Evidence
- Simulation scenes and logs covering stone placement, valid constructions, Grail elevation, return-zone status, and (if implemented) attack timing and scoring.
- Drawings and STEP models checked against the applicable rules and appendix dimensions.
