# eurobot_manipulation

This package controls the gripper that picks up and places game elements.

## Files

* `eurobot_manipulation/gripper_controller.py`: the gripper controller node.

## Sensors

The simulated robot has a left and a right gripper finger, each with a contact sensor. The bridges launch file in `eurobot_navigation` forwards them to ROS 2 as:

* `/gripper/left/contact`
* `/gripper/right/contact`

These topics let the controller know when a finger touches an object.

## Status

Manipulation is still a 2026 prototype. It has not been updated for the 2027 tasks (stones, Grail, construction yet). This is tracked in the open items of [overview.md](overview.md).

## Run it

Start the simulation and the bridges first, then build and source the workspace:

```
colcon build --base-paths src
source install/setup.bash
```
