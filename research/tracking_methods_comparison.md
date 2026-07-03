# Tracking Methods Comparison

## Goal

This document compares possible tracking methods for the person-following drone umbrella system.

The purpose is to decide which tracking method is most feasible for the first summer MVP prototype.

## Methods Compared

We considered three main tracking methods:

1. GPS-based tracking
2. Bluetooth-based tracking
3. Camera-based tracking using OpenCV and YOLO

## Comparison Table

| Method | Main Idea | Advantages | Limitations | MVP Suitability |
|---|---|---|---|---|
| GPS | The drone follows the user's GPS location. | Useful for outdoor rough positioning; simple concept. | Accuracy may not be enough for close-range following; poor indoor performance. | Medium |
| Bluetooth | The drone estimates user proximity using Bluetooth signal strength or a beacon. | Low cost; simple hardware; useful for user identification or proximity detection. | RSSI is unstable; direction is difficult to estimate; affected by obstacles. | Low to Medium |
| Camera + OpenCV/YOLO | The drone detects the person through a camera and estimates their relative position. | Provides left/right position and approximate distance; strong visual demo; suitable for software prototype. | Affected by lighting, occlusion, and compute speed. | High |

## MVP Decision

For the first MVP prototype, we decided to use camera-based tracking with OpenCV and YOLO.

The main reason is that camera-based tracking can directly estimate the user's relative position in the frame, such as whether the person is on the left, right, near, or far. This makes it more suitable for demonstrating person-following behavior.

GPS and Bluetooth may still be considered in future versions as supporting methods for rough positioning, proximity detection, or user identification.
