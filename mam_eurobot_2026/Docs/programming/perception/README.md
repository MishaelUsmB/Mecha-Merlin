# Perception — eurobot_perception

**Goal**: detect 2027 cardboard stones from ArUco ID **13** and publish robot-relative positions in meters. Legacy blue/yellow crate IDs remain recognized for the old simulation.

## Nodes
- **aruco_crate_perception** → publishes `CrateDetectionArray` with 2027 stones labelled `"stone"`
- **pantry_detection_node** → publishes `PantryDetectionArray` (with unique IDs)

## Approach
- ArUco detection using a configurable dictionary; the 2027 rules specify marker ID 13 but do not specify the dictionary or physical marker size.
- Repeated marker IDs are tracked by spatial proximity so separate stones are not merged into one detection.
- The default target label is `"stone"`; set `team_color` to `"blue"` or `"yellow"` for legacy crate markers.

The 2027 stone dimensions are **320 × 110 × 110 mm**. Confirm the printed marker size and dictionary against the physical field elements before using pose estimates for manipulation.

_Reference: Eurobot Perception Package Documentation.pdf._
