# Troubleshooting and Test Notes

## 1. Purpose

This document records problems, observations and corrective actions encountered
during the UAV Edge-AI hardware and video-stream investigation.

Only experimentally observed issues and their corresponding actions are
recorded here.

## 2. C12 Video Display Investigation

### 2.1 Initial Video Display

During bench testing, the SIYI C12 camera was successfully connected to the
SIYI/MK15 system and live video was observed through the available SkyDroid
gimbal application.

The initial observation confirmed that the camera and ground-side video
system were operating, but did not by itself establish the video path to the
Jetson.

### 2.2 FPV Application Video Configuration

The SIYI FPV application provided Camera 1 and Camera 2 options.

RTSP stream addresses obtained from the SIYI gimbal application were tested
using these camera options.

The two identified streams were:

- Stream 1: RGB
- Stream 2: Thermal

Both corresponding video feeds were successfully displayed through the FPV
application.

### 2.3 RTSP Investigation

RTSP stream addresses were identified during the investigation.

The addresses contained a private IP address and port and were successfully
used by the tested SIYI FPV configuration.

The exact RTSP URLs are not recorded in this document.

The direct connection of these streams to the NVIDIA Jetson Orin Nano remains
to be verified.

## 3. Video Codec Observation

During the MK15 video test, the debug information displayed H.265/HEVC
decoding information.

The displayed statistics also showed a Loss Count of 0 at the time of the
observation.

This is recorded as an observation from the tested MK15 configuration.
Resolution, FPS and end-to-end latency were not inferred from the debug
display and still require measurement.

## 4. Current Known Limitations

The following items remain unresolved or require further experimental
verification:

- Direct RTSP reception on the Jetson
- H.265/HEVC decoding on the Jetson
- Actual RGB resolution
- Actual thermal resolution
- RGB input FPS
- Thermal input FPS
- End-to-end video latency
- Stream stability and recovery behaviour
- Jetson-side resource utilization during video processing

## 5. Next Troubleshooting Stage

The next troubleshooting stage will focus on the Jetson video-input path.

The planned investigation is:

1. Verify network reachability of the RTSP source from the Jetson.
2. Test RTSP stream access from the Jetson.
3. Verify H.265/HEVC decoding.
4. Display the received stream on the Jetson.
5. Measure resolution and FPS.
6. Measure latency.
7. Test behaviour after temporary stream interruption.
8. Record any errors and corrective actions.