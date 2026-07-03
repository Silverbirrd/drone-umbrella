# Drone Umbrella

A research and prototype project for a person-following drone umbrella system.

## Project Goal

The goal of this project is to research and prototype a drone-based umbrella system that can follow a user and provide portable shade or rain protection.

For the first MVP prototype, we plan to focus on camera-based tracking. The system will use a camera to detect a person, estimate the person's relative position, and generate basic movement commands for a drone or simulation.

## MVP Tracking Method

The main tracking method for the first prototype will be camera-based tracking using OpenCV and YOLO.

The basic pipeline is:

Camera → OpenCV → YOLO → Person Position Estimation → Tracking Controller → Drone Command

OpenCV will be used to capture and process camera frames. YOLO will be used to detect the person in the frame. The detected bounding box will then be converted into position information such as left/right offset and approximate distance.

## Basic Control Logic

The first version of the tracking logic will be simple:

- If the person is on the left side of the frame, the drone should move left.
- If the person is on the right side of the frame, the drone should move right.
- If the person appears too far away, the drone should move forward.
- If the person appears too close, the drone should move backward.
- If no person is detected, the drone should stop or hover.

## Future Tracking Extensions

GPS and Bluetooth were also considered as possible tracking methods.

They may be useful in future versions for rough positioning, proximity detection, or user identification. However, they are not selected as the main tracking method for the first MVP because they may not provide reliable close-range relative position information.

## Current Research Focus

The current research focuses on:

- OpenCV camera input
- YOLO person detection
- Bounding box position estimation
- Basic tracking control logic
- ROS2 integration plan
- Drone simulation or hardware options

## Possible Technology Stack

- Python
- OpenCV
- YOLO
- ROS2
- PX4 / Gazebo simulation
- Raspberry Pi or Jetson for future onboard computing
- Pixhawk or other flight controller for future drone hardware

## Current Stage

- [x] Create GitHub repository
- [x] Define initial project goal
- [x] Compare GPS, Bluetooth, and camera-based tracking
- [x] Select camera-based tracking as the MVP direction
- [x] Research OpenCV and YOLO
- [ ] Design the first camera tracking prototype
- [ ] Build a webcam-based person detection demo
- [ ] Convert the demo into a ROS2 node
- [ ] Test basic tracking command output
- [ ] Explore drone simulation or hardware integration

## Repository Structure

```text
drone-umbrella/
├── README.md
├── .gitignore
├── research/
│   ├── tracking_methods_comparison.md
│   ├── camera_tracking_plan.md
│   └── system_architecture_options.md
├── vision_tests/
│   └── yolo_webcam_test.py
└── requirements.txt
