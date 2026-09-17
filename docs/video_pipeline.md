# Video Pipeline Investigation

## 1. Objective

This document records the experimental investigation of the SIYI C12 video
pipeline and the planned path for delivering the video stream to the NVIDIA
Jetson Orin Nano for edge-AI processing.

The purpose of this investigation is to verify the actual video interfaces,
streaming method, network configuration, video format and processing path
before implementing the AI pipeline.

No video transport or interface is assumed to be working unless it has been
experimentally verified.

## 2. Current Bench-Test Setup

The current bench-test system consists of:

- SIYI C12 camera
- SIYI MK15 ground controller
- SIYI FPV application
- SIYI gimbal application
- NVIDIA Jetson Orin Nano for the planned edge-processing stage

The MK15 was connected wirelessly during the video-stream investigation.

## 3. Experimentally Verified Video Streams

During bench testing, two RTSP streams were identified through the SIYI
gimbal application.

| Stream | Camera Feed | Verification |
|---|---|---|
| RTSP Stream 1 | RGB | Successfully displayed |
| RTSP Stream 2 | Thermal | Successfully displayed |

The corresponding RTSP stream addresses were entered into the available
Camera 1 and Camera 2 options in the SIYI FPV application.

Both the RGB and thermal feeds were successfully displayed.

This confirms that the identified RTSP streams can be accessed by the SIYI
FPV application under the tested bench configuration.

## 4. Video Codec Observation

During the observed video test, the MK15 displayed:

- Decode type: H.265
- H.265/HEVC decoding information was visible in the MK15 debug display.
- Loss Count: 0 at the time of observation.

The observed H.265/HEVC information is recorded as an experimental
observation from the MK15 display.

The exact encoding parameters and stream configuration still require
further verification.

## 5. Parameters Still to Be Measured

The following parameters have not yet been experimentally measured:

| Parameter | Status |
|---|---|
| Stream 1 IP address | Recorded during testing |
| Stream 1 port | Recorded during testing |
| Stream 2 IP address | Recorded during testing |
| Stream 2 port | Recorded during testing |
| RGB resolution | Not yet measured |
| Thermal resolution | Not yet measured |
| RGB input FPS | Not yet measured |
| Thermal input FPS | Not yet measured |
| End-to-end latency | Not yet measured |
| Jetson RTSP reception | Not yet verified |
| Jetson video decoding | Not yet verified |

Exact RTSP URLs are not included in this documentation at the current
stage.

## 6. Current Video Path

The experimentally observed portion of the video path is:

```text
SIYI C12
   │
   ├── RGB → RTSP Stream 1
   │
   └── Thermal → RTSP Stream 2
             │
             ▼
      SIYI Video System
             │
             ▼
           MK15
             │
             ▼
       SIYI FPV App
             │
             ├── RGB video
             │
             └── Thermal video