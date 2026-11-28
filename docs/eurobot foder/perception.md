# eurobot_perception

This package finds game elements in the camera image. For 2027 the main node detects the stones using ArUco markers.

## Files

In `eurobot_perception/eurobot_perception/`:
* `aruco_crate_perception.py`: the production ArUco node. It recognizes the 2027 stones (ArUco ID 13) and keeps the older crate IDs working.
* `crate_perception.py` and `crate_perception_V2.py`: earlier crate perception nodes. V2 is the improved version of the first.
* `crate_detector.py`: crate detection helper.
* `color_identifier.py`: identifies the color of a detected object.
* `pantry_detection.py`: detects pantry items.
* `RotationTester.py`: a test tool for checking marker rotation.

Launch files in `launch/`:
* `perception.launch.py`: starts perception.
* `aruco_crate_perception.launch.py`: starts the ArUco node with its parameter file.

Parameters in `config/aruco_crate_perception_params.yaml`.

## Parameters

The ArUco node reads these values from the yaml file:

* `camera_topic`: the camera image topic, set to `/camera`.
* `team_color`: the target label. For 2027 it is `stone`. Use `all` to publish every recognized marker.
* `aruco_dict`: the ArUco dictionary, currently `DICT_4X4_50`.
* `marker_size`: the physical marker size in meters, currently `0.040`.
* `min_confidence`: the lowest confidence to accept a detection, currently `0.35`. A lower value gives more detections but more false positives. It must match the threshold used by the mission controller.
* `max_distance`: detections farther than this many meters are ignored, currently `3.0`.
* `base_frame`: the robot base frame, `base_link`.
* `visualize`: when `true`, the node publishes an image with detected markers drawn on it, on the `/crate/image_debug` topic. Turn it off for the competition to save processing time.

## Run it

```
colcon build --base-paths src
source install/setup.bash
ros2 launch eurobot_perception aruco_crate_perception.launch.py
```

## Open items

* The 2027 rules specify ID 13 for the stones but not a dictionary. Verify the dictionary with the organizers before relying on `DICT_4X4_50`.
* The marker size is provisional. Measure it on an official stone and update `marker_size`.
* The design notes are in `mam_eurobot_2027/Docs/programming/perception/`.
