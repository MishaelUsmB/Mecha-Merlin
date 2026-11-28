# Hardware and project files

The top level folder `mam_eurobot_2027/` holds everything that is not ROS code. It has three parts.

## Docs

Design documents and requirements:
* `Docs/requirements/README.md`: the system requirements for Eurobot 2027, based on the Eurobot and Eurobot Junior 2027 Rules, Official 1.0.
* `Docs/programming/navigation/`: the navigation design notes.
* `Docs/programming/perception/`: the perception design notes, including the ArUco crate perception design.
* `Docs/demo/`: demo recordings.

## Mechanical

* `Mechanical/Robot part/`: mechanical files and recordings for the robot parts.

## Electronics

* `Electronics/schematics/`: the KiCad schematics for the power and motion board (`Power&MotionV2`) and the sensor input and output board (`Sensor_IO_V1`), plus the electronics design document.
* `Electronics/bom/`: the bill of materials spreadsheets (BOM V2, several updated versions).

## A note on dates

Several of these files carry 2026 dates and names, because they were made for the 2026 build. Check them against the 2027 rules before reusing them. The most recent bill of materials is the one with the latest date in its file name.
