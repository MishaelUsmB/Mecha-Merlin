# eurobot_interfaces

This package holds the custom ROS 2 message types that the other packages use to talk to each other. It contains no nodes. It is a message package built with `CMakeLists.txt` and `package.xml`.

## Messages

All messages are in the `msg` folder.

* `CrateDetection.msg`: one detected crate or stone.
* `CrateDetectionArray.msg`: a list of crate detections, published together.
* `PantryDetection.msg`: one detected pantry item.
* `PantryDetectionArray.msg`: a list of pantry detections, published together.

To see the exact fields of any message once the workspace is built and sourced:

```
ros2 interface show eurobot_interfaces/msg/CrateDetection
```

## Who uses it

* `eurobot_perception` publishes detections with these types.
* `eurobot_navigation` and the task manager read them to choose targets.

## Adding a new message

1. Create the `.msg` file in `msg/`.
2. Add its path to the message list in `CMakeLists.txt`.
3. Rebuild with `colcon build --base-paths src` and source `install/setup.bash`.
