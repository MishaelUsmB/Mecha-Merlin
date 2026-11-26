# Navigation & Mission — eurobot_navigation

**Goal**: autonomous SLAM/localization, path planning, and a basic approach behavior for Eurobot 2027 stones, built on ROS 2 Nav2.

## Components
- **SLAM** (slam_toolbox wrapper) → /map occupancy grid  
- **Localization** (AMCL wrapper) → /amcl_pose  
- **Global planner** (Nav2 planner_server wrapper) → /plan  
- **Local planner** (Nav2 controller_server wrapper) → /cmd_vel  
- **Mission Controller** (custom): targets the nearest detected stone and approaches it.

## Key topic flows
- **/scan → SLAM/AMCL → /amcl_pose** (pose)  
- **Task Manager → /task_manager/nav_goal → Nav2 → /cmd_vel**  
- Integrates **/crate/detections** (stone label `"stone"`; legacy topic name retained) from perception.

The current controller's grab state is still a placeholder. Construction, Grail handling, return-zone logic, and the 2027 arena model remain unimplemented.

_Reference: Eurobot Navigation Package Documentation.pdf._
