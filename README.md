# Marker Tracker Project

A ROS package designed for marker detection, tracking, and alignment using a robot’s camera system. The package enables the robot to identify unique markers placed in a circular configuration around it, navigate towards them, and visually process them on its camera feed. The implementation provides two distinct operational modes:

1. **Full Chassis Rotation**: The robot’s entire chassis rotates to detect and align with markers. (Handled by `camera_fix.py`)
2. **Camera-Only Rotation**: The camera rotates independently, leaving the robot’s chassis stationary. (Handled by `camera_rotating.py`)

---
## Table of Contents

- Features
- Dependencies
- Setup and Installation
- Usage Instructions
- ROS Topics
- Code Overview
- Author

---
## Features

- Detects unique markers and identifies them by their IDs.
- Tracks the location of each marker and aligns the camera with the detected markers.
- Highlights detected markers by drawing a circle around them in the processed camera feed.
- Facilitates sequential marker detection and alignment by rotating the robot or camera.
- Stops rotation once all markers are identified and processed.

---
## Dependencies

Ensure the following software and libraries are installed:

### Required Software

- **Python 3.x**
- **ROS Noetic**

### Python Libraries

Install the necessary Python libraries with:

```bash
pip install numpy scipy opencv-python imutils
```

### Additional Files

This package includes the necessary ArUco marker detection library and URDF files required for marker tracking. No external repositories or additional manual substitutions are needed.

---
## Setup and Installation

1. **Clone this repository into your ROS workspace:**
   ```bash
   git clone https://github.com/mohammadhoseinbaba/Experimental-first
   ```

2. **Build the workspace:**
   ```bash
   catkin_make
   ```

---
## Usage Instructions

### Running with Full Chassis Rotation
To enable marker detection with full chassis rotation, execute:

```bash
roslaunch robot_urdf launcher1.launch
```

### Running with Camera-Only Rotation
For marker detection with only the camera rotating, execute:

```bash
roslaunch robot_urdf launcher2.launch
```

---
## ROS Topics

### Published Topics

1. **`/output/image_raw/compressed`**
   - **Message Type:** `sensor_msgs/CompressedImage`
   - **Description:** Publishes the processed camera feed with detected markers visually highlighted.

2. **`/cmd_vel`**
   - **Message Type:** `geometry_msgs/Twist`
   - **Description:** Publishes velocity commands to rotate the robot or the camera to align with markers.

### Subscribed Topics

1. **`/robot/camera1/image_raw/compressed`**
   - **Message Type:** `sensor_msgs/CompressedImage`
   - **Description:** Receives raw camera feed for marker detection.

2. **`/robot/camera1/camera_info`**
   - **Message Type:** `sensor_msgs/CameraInfo`
   - **Description:** Provides camera resolution and focal properties.

3. **`/marker/id_number`**
   - **Message Type:** `std_msgs/Int32`
   - **Description:** Receives the unique ID of the detected marker.

4. **`/marker/center_loc`**
   - **Message Type:** `geometry_msgs/Point`
   - **Description:** Provides the center coordinates of the detected marker.

---
Mohammadhossein baba - S5919466

