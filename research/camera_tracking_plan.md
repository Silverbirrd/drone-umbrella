# Camera Tracking Plan

## Goal

The goal of the camera tracking system is to detect a person in real time and estimate their relative position in the camera frame.

This position information will later be converted into basic drone movement commands.

## System Pipeline

Camera → OpenCV → YOLO → Bounding Box → Person Position Estimation → Tracking Controller → Drone Command

## OpenCV Role

OpenCV will be used to:

- Capture camera frames
- Display the video feed
- Draw bounding boxes and center points
- Show detection information on screen

## YOLO Role

YOLO will be used to detect the person in the camera frame.

The detector should output:

- Whether a person is detected
- Bounding box coordinates
- Confidence score
- Person center position
- Bounding box area

## Position Estimation

The person's center position can be calculated from the bounding box:

center_x = (x1 + x2) / 2  
center_y = (y1 + y2) / 2

The offset from the image center can be calculated as:

offset_x = center_x - image_center_x  
offset_y = center_y - image_center_y

The bounding box area can be used as a rough estimate of distance:

box_area = (x2 - x1) × (y2 - y1)

## Basic Interpretation

- Positive offset_x: person is on the right side of the frame
- Negative offset_x: person is on the left side of the frame
- Small box_area: person is far away
- Large box_area: person is close

## Basic Control Logic

- Person on the left → move left
- Person on the right → move right
- Person too far → move forward
- Person too close → move backward
- No person detected → stop or hover

## First Prototype Goal

The first software prototype should:

- Open the webcam
- Detect a person using YOLO
- Draw a bounding box
- Calculate center_x and center_y
- Calculate offset_x and offset_y
- Print or display the basic movement command

## Next Steps

- Test webcam input with OpenCV
- Run YOLO person detection
- Calculate person offset
- Create a simple command output
- Convert the program into a ROS2 node later
