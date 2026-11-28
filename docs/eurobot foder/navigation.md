# eurobot_navigation

This package gets the robot around the arena: mapping, localization, path planning and task sequencing. It also holds the launch file that connects Gazebo to ROS 2.

## Nodes

In `eurobot_navigation/eurobot_navigation/`:
* `slam_node.py`: builds the map of the arena.
* `localization_node.py`: estimates where the robot is.
* `nav2_global_planner.py`: plans the full path to a goal.
* `nav2_local_planner.py`: follows the path and avoids obstacles close by.
* `scan_frame_fixer.py`: corrects the frame of the laser scan so it matches the robot frames.
* `simple_crate_navigator.py`: drives the robot to a detected crate.
* `task_manager.py`: decides what the robot does next.
* `teleop_keyboard.py`: drives the robot by hand from the keyboard, for testing.

## Configuration

In `config/`:
* `nav2_params.yaml`: Nav2 parameters.
* `mapper_params_online_async.yaml`: parameters for the online asynchronous mapper.

## Launch files

In `launch/`:
* `bridges.launch.py`: bridges Gazebo topics to ROS 2. It carries the joint states and the contact sensors on the left and right gripper fingers, which appear as `/gripper/left/contact` and `/gripper/right/contact`.
* `mapping_navigation.launch.py`: mapping together with navigation.
* `navigation.launch.py`: navigation on an existing map.
* `online_async_launch.py`: starts the online asynchronous mapper.

## Important: the world name

`bridges.launch.py` refers to the Gazebo world by name, in paths that start with `/world/eurobot_2027_arena/model/simple_robot/...`. That name must match the world name inside `src/mam_eurobot_2027/worlds/arena_world.sdf`. If one is changed, change the other too. If they differ, the bridges stop working without an obvious error.

## Run it

```
colcon build --base-paths src
source install/setup.bash
ros2 launch eurobot_navigation bridges.launch.py
ros2 launch eurobot_navigation navigation.launch.py
```

Start the simulation first, so the bridges have something to connect to. See [simulation.md](simulation.md).

## Notes

* The design notes are in `mam_eurobot_2027/Docs/programming/navigation/`.
* The package has the standard ROS 2 style tests in `test/` (copyright, flake8, pep257).
