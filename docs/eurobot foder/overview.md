# Eurobot 2027 Project Overview

This repository holds our robot software and project files for Eurobot 2027. It is built on the baseline repository from the Master Advanced Mechatronics program at Polytech Annecy Chambéry (courses PROJ703 and PROJ903).

The 2027 challenge: build Camelot, raise the team's Grail, return the main robot to its throne room, and optionally attack with SIMAs and cannonballs. The requirements follow the Eurobot and Eurobot Junior 2027 Rules, Official 1.0. Rules can be clarified during the year, so always check the current official version and the national organizer notices before changing a design.

## Current status

The migration from the 2026 version is partly done.

Working for 2027:
* The ArUco detector recognizes the 2027 stones (ArUco ID 13) and the controller can target them.

Still 2026 prototypes or not implemented yet:
* The arena (2027 field layout, stones, ramparts, Grail and attack elements)
* Manipulation
* Construction
* Grail handling
* Scoring

The detailed 2027 requirements are in `mam_eurobot_2027/Docs/requirements/README.md`.

## Repository layout

ROS 2 packages, all inside `src/`:
* `eurobot_interfaces`: the custom ROS messages shared by the other packages. See [interfaces.md](interfaces.md).
* `eurobot_perception`: camera detection of stones, crates and pantry items. See [perception.md](perception.md).
* `eurobot_navigation`: mapping, localization, path planning and the task manager. See [navigation.md](navigation.md).
* `eurobot_manipulation`: the gripper controller. See [manipulation.md](manipulation.md).
* `mam_eurobot_2027`: the Gazebo simulation (robot model, arena world, meshes). See [simulation.md](simulation.md).

Project files that are not ROS code, in the top level folder `mam_eurobot_2027/`:
* `Docs`: design documents and requirements
* `Mechanical`: robot mechanical files
* `Electronics`: schematics and bills of materials

See [hardware.md](hardware.md).

## How the parts fit together

1. The simulation provides the arena, the robot and its camera and sensors.
2. The bridges launch file connects Gazebo topics to ROS 2 topics.
3. Perception reads the camera image and publishes detections using the message types from `eurobot_interfaces`.
4. Navigation uses the laser scan and the detections to localize, plan paths and drive to targets, with the task manager deciding what to do next.
5. Manipulation controls the gripper, using the finger contact sensors.

## Setup

The project is meant to run as a Dev Container in VS Code, with ROS 2 Humble and Ignition Gazebo Fortress on Ubuntu Jammy (22.04). The container files are in the `.devcontainer` folder.

Build from the repository root:

```
colcon build --base-paths src
source install/setup.bash
```

Launch files live in the `launch` folder of each package. The pattern is:

```
ros2 launch <package_name> <launch_file>
```

For example: `ros2 launch eurobot_perception perception.launch.py`.

## Open items

* Confirm the ArUco dictionary with the organizers. The 2027 rules give ID 13 but do not name a dictionary.
* Confirm the physical marker size on the official 2027 stones. The value in the parameter file is provisional.
* Build the 2027 field layout in the simulation world.
* Update manipulation, construction, Grail handling and scoring for the 2027 tasks.
