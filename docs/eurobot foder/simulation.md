# mam_eurobot_2027 (simulation)

This package contains the Gazebo simulation of the arena and the robot. It is a ROS 2 package built with CMake. Not to be confused with the top level `mam_eurobot_2027/` folder, which holds documents, mechanical files and electronics (see [hardware.md](hardware.md)).

## Stack

ROS 2 Humble with Ignition Gazebo Fortress on Ubuntu Jammy (22.04), run inside the project Dev Container.

## Contents

* `worlds/arena_world.sdf`: the arena world. The world name is `eurobot_2027_arena`.
* `models/`: the models placed in the world. At the moment these are `simple_robot` (the reference robot), `crate_yellow` and `mat`.
* `urdf/`: the robot description.
* `meshes/`: 3D meshes used by the models.
* `launch/`: launch files for the simulation.
* `package.xml`, `CMakeLists.txt` and `setup.py`: package definition.
* `LICENSE`: the license of the template this simulation comes from.

## The robot model

`simple_robot` has a left and a right gripper finger. Each finger has a contact sensor, and the robot publishes its joint states. The bridges launch file in `eurobot_navigation` connects these to ROS 2. See [navigation.md](navigation.md).

## The world name

The name `eurobot_2027_arena` is used in `bridges.launch.py` as well. If you rename the world, update both places.

## Status and open items

The arena is still the 2026 layout. The 2027 field layout, stones, ramparts, Grail and attack elements still need to be built. This is tracked in [overview.md](overview.md).

The stone detection tests need the 2027 stones in the world, with ArUco ID 13 on them. See [perception.md](perception.md).
