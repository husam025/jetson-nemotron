# System Architecture

## 1. Project Overview

This project focuses on developing an edge-AI pipeline for a UAV-based
disaster-response system. The system uses a SIYI C12 camera and SIYI MK15
ground controller together with an NVIDIA Jetson Orin Nano for on-device
video processing and AI inference.

The intended processing pipeline is to obtain the UAV camera video at the
Jetson, process the incoming frames locally, perform object detection using
a YOLO-based model, and subsequently support object tracking and
mission-level results.

The initial development and validation are being carried out through
controlled bench and laboratory testing before any autonomous flight
integration.


## 2. UAV Platform

The UAV platform used for the project consists of the following major
components:

### 2.1 UAV Frame

- Platform: TBS500
- Role: UAV platform carrying the flight controller, camera and associated
  communication hardware.

### 2.2 Flight Controller

- Flight controller: Pix4 / Orange Cube
- Role: Flight-control and UAV-side control system.

### 2.3 SIYI C12 Camera

- Camera: SIYI C12
- Role: Primary onboard imaging source for the project.
- Intended use: Provide visual data for downstream video processing and
  edge-AI inference.

### 2.4 SIYI MK15

- Ground controller: SIYI MK15
- Role: Ground-side controller used to operate and monitor the UAV system
  and access the camera/video system.

### 2.5 Current Video Observation

During bench testing, video from the SIYI C12 camera was successfully
observed on the SIYI MK15 through the SIYI FPV application.

Two RTSP video streams were identified through the SIYI gimbal application:

- RTSP Stream 1: RGB camera feed
- RTSP Stream 2: Thermal camera feed

The RTSP addresses were observed in the form of a private IP address and
port. The corresponding stream addresses were entered into the SIYI FPV
application using the available Camera 1 and Camera 2 options, and the
corresponding live video feeds were successfully displayed.

During the observed bench test, the MK15 displayed H.265/HEVC decoding
information. The displayed stream statistics also showed a Loss Count of 0
at the time of observation.

Direct reception and decoding of these RTSP streams by the NVIDIA Jetson
Orin Nano has not yet been verified. Exact stream resolution, input frame
rate
and end-to-end video latency also remain to be measured.

## 3. Edge Computing Platform

### 3.1 NVIDIA Jetson Orin Nano

The NVIDIA Jetson Orin Nano is used as the edge-computing platform for
the AI processing stage of the UAV system.

Its intended role is to receive the UAV video stream, process video frames
locally, and run AI inference without relying on a remote cloud server.

### 3.2 Jetson Software Environment

The current Jetson environment has been prepared and verified with the
following components:

- Operating System: Ubuntu 22.04
- JetPack: 6.2
- L4T: R36.4.3
- CPU architecture: ARM64 (aarch64)
- ROS 2: Humble
- CUDA: Installed and available in the Jetson environment
- Ollama: Installed for local AI experimentation

### 3.3 ROS 2 and Sensor Integration

ROS 2 Humble has been installed and basic ROS 2 communication has been
verified on the Jetson.

The Livox MID-360 LiDAR has also been connected and made available through
ROS 2 for further perception and robotics development.

These components provide the foundation for integrating perception,
sensor processing and AI capabilities on the edge-computing platform.

## 4. Current System Architecture

## 4. Current System Architecture

The current system consists of an air-side UAV platform, the SIYI C12
camera, the SIYI MK15 ground-control/video system, and an NVIDIA Jetson
Orin Nano edge-computing platform.

The C12 RGB and thermal video streams have been experimentally identified
as RTSP streams. The RGB feed is available through RTSP Stream 1 and the
thermal feed through RTSP Stream 2. These streams have been successfully
used by the SIYI FPV application during bench testing.

The direct network/video path from the SIYI system to the Jetson remains
under investigation.

```text
                    UAV / AIR SIDE

        ┌──────────────────────────────┐
        │            TBS500            │
        │                              │
        │   ┌──────────────────────┐   │
        │   │ Pix4 / Orange Cube    │   │
        │   │ Flight Controller     │   │
        │   └──────────────────────┘   │
        │                              │
        │   ┌──────────────────────┐   │
        │   │ SIYI C12 Camera       │   │
        │   │                      │   │
        │   │ RGB → RTSP Stream 1  │   │
        │   │ Thermal → RTSP Stream 2│  │
        │   └──────────────────────┘   │
        └──────────────┬───────────────┘
                       │
                       │ SIYI Video /
                       │ Communication Link
                       ▼
        ┌──────────────────────────────┐
        │          SIYI MK15           │
        │      Ground Controller       │
        │                              │
        │  SIYI FPV App                │
        │  Live RGB / Thermal Video   │
        └──────────────┬───────────────┘
                       │
                       │ RTSP access to Jetson
                       │ under investigation
                       ▼
        ┌──────────────────────────────┐
        │     NVIDIA Jetson Orin Nano  │
        │                              │
        │  Video Acquisition / Decode  │
        │             ↓                │
        │      AI Inference            │
        │             ↓                │
        │    Object Detection          │
        │             ↓                │
        │     Object Tracking          │
        └──────────────────────────────┘

       
       
       
       
       
       
       
 ## 5. Video and AI Processing Pipeline

## 5. Video and AI Processing Pipeline

The edge-AI pipeline is designed to process video from the SIYI C12 locally
on the NVIDIA Jetson Orin Nano.

The C12 currently provides two experimentally identified RTSP streams:

- Stream 1: RGB
- Stream 2: Thermal

The RTSP streams have been successfully displayed through the SIYI FPV
application during bench testing. Direct reception of these streams by the
Jetson remains to be verified.

### 5.1 Current and Planned Pipeline

```text
SIYI C12 Camera
       │
       ├── RGB → RTSP Stream 1
       │
       └── Thermal → RTSP Stream 2
                    │
                    ▼
             SIYI / MK15 System
                    │
                    ▼
             RTSP Access to Jetson
                    │
              Under Verification
                    ▼
          Video Acquisition / Decoding
                    │
                    ▼
             Frame Processing
                    │
                    ▼
            YOLO Object Detection
                    │
                    ▼
              Object Tracking
                    │
                    ▼
           Mission-Level Results

## 6. Milestone Status

| Milestone | Description | Status |
|---|---|---|
| M1 | Hardware familiarisation | Completed |
| M2 | C12/MK15 bench testing |Completed |
| M3 | Jetson video input | In progress |
| M4 | YOLO detection | Planned |
| M5 | Object tracking | Planned |
| M6 | Performance optimization | Planned |
| M7 | Integrated demonstration | Planned |

### M1 Completion

### M1 Completion

The major UAV, SIYI and edge-computing components have been identified and
documented. The Jetson Orin Nano environment has also been prepared for
subsequent video-processing and AI development.

During subsequent C12/MK15 bench testing, the RGB and thermal RTSP streams
were identified and successfully displayed through the SIYI FPV application.
H.265/HEVC decoding information was observed during the test.

The direct RTSP video path to the Jetson, along with stream resolution,
input FPS and end-to-end latency, remains to be verified and measured.