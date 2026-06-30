# Drone Umbrella

A research and prototype project for a person-following drone umbrella system.

## Project Goal

The goal of this project is to research and prototype a drone-based umbrella system that can follow a user and provide portable shade or rain protection.

At the current stage, we are comparing different tracking methods and evaluating which approach is most feasible for a summer prototype.

## Tracking Methods Under Consideration

We are currently comparing three possible tracking approaches:

1. GPS-based tracking
2. Bluetooth-based tracking
3. Camera-based tracking using OpenCV and YOLO

## Current Research Questions

- Which tracking method is most accurate for following a walking person?
- Which method is easiest to prototype within the summer timeline?
- Which method has the lowest cost and hardware complexity?
- Which method is safest for drone movement?
- Can different methods be combined, such as GPS for rough positioning and camera vision for final alignment?

## Current Stage

- [ ] Compare GPS, Bluetooth, and camera-based tracking
- [ ] Define the MVP system architecture
- [ ] Research hardware options
- [ ] Research software tools
- [ ] Decide the final tracking method
- [ ] Build the first prototype demo

## Possible Technology Stack

- Python
- OpenCV
- YOLO
- ROS2
- PX4 / Gazebo simulation
- GPS / Bluetooth modules if needed

## Notes

This repository is currently used for research, planning, and early prototype testing.
