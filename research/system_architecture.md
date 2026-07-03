# System Architecture

## Goal

This document describes the planned system architecture for the drone umbrella MVP prototype.

The first prototype will focus on camera-based person tracking and basic movement command generation.

## MVP Architecture

Camera → OpenCV → YOLO → Person Position Estimation → Tracking Controller → Drone Command

## Module Breakdown

### 1. Camera Input Module

The camera input module captures real-time video frames.

Possible hardware:

- Laptop webcam
- USB camera
- Raspberry Pi camera in future versions

### 2. Person Detection Module

The person detection module uses YOLO to detect a person in the frame.

Main outputs:

- Detection status
- Bounding box coordinates
- Confidence score

### 3. Position Estimation Module

This module converts the bounding box into useful tracking information.

Main outputs:

- offset_x
- offset_y
- box_area
- approximate distance state

### 4. Tracking Controller Module

The tracking controller converts position information into movement commands.

Example commands:

- move left
- move right
- move forward
- move backward
- stop or hover

### 5. Safety Logic Module

The safety logic should prevent unsafe behavior.

Possible rules:

- If no person is detected, stop or hover.
- If the person is too close, stop or move backward.
- Limit maximum movement speed.
- Avoid testing near people’s head or face.
- Keep manual override available during drone testing.

### 6. Drone Interface Module

This module will later send commands to a drone or simulation.

Possible future options:

- Command visualization only
- ROS2 topic output
- PX4/Gazebo simulation
- Small programmable drone
- Pixhawk-based drone platform

## First MVP Scope

The first MVP does not need to control a real drone immediately.

The first goal is to complete this software chain:

Camera → YOLO Detection → Person Offset → Basic Command Output

## Future Extension

In future versions, the system may integrate:

- ROS2 communication
- PX4/Gazebo simulation
- Raspberry Pi or Jetson onboard computing
- Pixhawk flight controller
- GPS or Bluetooth as supporting tracking methods
