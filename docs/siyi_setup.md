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

The C12 camera has been identified and tested as part of the initial
system familiarisation.

During bench testing, camera video was observed through the available
SIYI/MK15 system.

Further investigation is required to determine the exact video transport
method and the interface through which the stream can be accessed by an
external processing platform such as the Jetson.

## 3. SIYI MK15 Ground Controller

### 3.1 Role

The SIYI MK15 is the ground-side controller used to operate and monitor
the UAV system and interact with the SIYI camera/video system.

It provides the ground-side interface through which the camera system can
be monitored during bench testing.

### 3.2 Current Video Observation

During the initial bench test, the C12 camera video was successfully
observed on the MK15 through the SkyDroid gimbal application.

This confirms that the camera and ground-side system can establish a
working video display under the tested setup.

The exact transport mechanism used by the video system has not yet been
confirmed. RTSP and other possible video-access methods will be
investigated separately.

### 3.3 Connectivity Status

The physical and network interfaces between the C12, MK15 and external
processing hardware are being documented and verified progressively.

At the current stage, no specific RTSP URL, codec, IP configuration or
video-stream endpoint is recorded as confirmed.

These parameters will be added after experimental verification.

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
|---|---|
| C12 identified | Completed |
| MK15 identified | Completed |
| C12 video operation observed | Completed |
| Video displayed on MK15 | Completed |
| Exact video transport protocol | Under investigation |
| RTSP availability | Under investigation |
| Video stream endpoint/URL | Not yet verified |
| Codec | Not yet verified |
| Resolution/FPS | To be recorded during video testing |
| Jetson video connection | Not yet established |

This table will be updated as the system is tested and verified.