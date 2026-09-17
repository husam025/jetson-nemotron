# SIYI C12 and MK15 Setup

## 1. Overview

The SIYI C12 and SIYI MK15 form the camera and ground-controller
components of the UAV system.

The C12 is used as the onboard imaging device, while the MK15 is used as
the ground-side controller for UAV operation, monitoring and access to the
camera/video system.

This document records the hardware identified during the initial
familiarisation and bench-testing stage, together with the currently
known setup and observations.

## 2. SIYI C12 Camera

### 2.1 Role

The SIYI C12 is the onboard camera used to provide visual data for the
UAV Edge-AI system.

The camera is intended to provide the video input that will eventually be
processed by the NVIDIA Jetson Orin Nano for object detection and tracking.

### 2.2 Current Status

### 2.2 Current Status

The C12 camera has been identified and tested as part of the system
familiarisation and bench-testing stage.

During bench testing, live video from the C12 was successfully observed
through the SIYI MK15 system.

Two RTSP video streams were identified through the SIYI gimbal application:

- RTSP Stream 1: RGB camera feed
- RTSP Stream 2: Thermal camera feed

The corresponding stream addresses were entered into the available Camera 1
and Camera 2 options in the SIYI FPV application, and both RGB and thermal
video feeds were successfully displayed.

Direct reception and decoding of these RTSP streams by the NVIDIA Jetson
Orin Nano has not yet been verified.

## 3. SIYI MK15 Ground Controller

### 3.1 Role

The SIYI MK15 is the ground-side controller used to operate and monitor
the UAV system and interact with the SIYI camera/video system.

It provides the ground-side interface through which the camera system can
be monitored during bench testing.

### 3.2 Current Video Observation

### 3.2 Current Video Observation

During bench testing, the C12 camera video was successfully observed on the
MK15 through the SIYI FPV application.

Two RTSP streams were identified through the SIYI gimbal application:

- Stream 1: RGB
- Stream 2: Thermal

The corresponding RTSP stream addresses were configured in the SIYI FPV
application using the available Camera 1 and Camera 2 options. Both streams
were successfully displayed during testing.

The MK15 also displayed H.265/HEVC decoding information during the observed
video test. The displayed stream statistics showed a Loss Count of 0 at the
time of observation.

The direct video path from the SIYI system to the Jetson remains under
investigation.

### 3.3 Connectivity Status

### 3.3 Connectivity Status

The C12/MK15 video system has been successfully tested using the available
wireless connection between the camera/video system and the MK15.

RTSP stream addresses were obtained during the bench investigation. The
identified streams correspond to:

- Stream 1: RGB
- Stream 2: Thermal

The RTSP addresses contain a private IP address and port and were successfully
used to display the corresponding feeds through the SIYI FPV application.

The exact network configuration and the method required for direct access
from the NVIDIA Jetson Orin Nano are still being investigated.

Resolution, input FPS and end-to-end video latency have not yet been
experimentally measured.

### 3.4 Documentation

The SIYI MK15 User Manual v1.9 is being used as a reference during the
hardware familiarisation and interface investigation.

The manual is used to identify relevant hardware capabilities and
interfaces before carrying out practical verification.

## 4. Interfaces and Documentation

### 4.1 Interfaces

The C12/MK15 system includes interfaces used for camera operation,
communication and video transmission. The exact interface used to provide
the video stream to the Jetson is still being investigated.

The following information is being recorded as part of the hardware
familiarisation and subsequent video-input investigation:

- Camera-to-ground-controller communication
- Ground-controller network connectivity
- Video output/access method
- Physical interfaces available for external devices
- Network parameters required for video access
- Video transport protocol
- Video codec
- Resolution and frame rate

Parameters that have not yet been experimentally verified are not treated
as confirmed system values.

### 4.2 Reference Documentation

The following documentation is being used during the project:

- SIYI MK15 User Manual v1.9
- Project assignment and hardware requirements
- Relevant SIYI documentation for video, communication and SDK/API
  investigation where required

The MK15 manual is used as a reference for understanding the controller,
its available interfaces and operating capabilities. Practical testing is
used to verify the behaviour of the actual hardware setup.

### 4.3 Verification Status

| Item | Current Status |
### 4.3 Verification Status

| Item | Current Status |
|---|---|
| C12 identified | Completed |
| MK15 identified | Completed |
| C12 video operation observed | Completed |
| Video displayed on MK15 | Completed |
| RGB RTSP stream identified | Completed |
| Thermal RTSP stream identified | Completed |
| RTSP stream addresses obtained | Completed |
| H.265/HEVC decoding observed on MK15 | Completed |
| Loss Count observed as 0 during test | Completed for observed test |
| Direct Jetson video connection | Not yet established |
| Jetson video decoding | Not yet verified |
| Resolution | Not yet measured |
| Input FPS | Not yet measured |
| End-to-end latency | Not yet measured |

This table will be updated as further video-input and Jetson integration
testing is performed.