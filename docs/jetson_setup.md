# Jetson Setup

## 1. Platform Overview

The NVIDIA Jetson Orin Nano Developer Kit is being used as the edge
computing platform for the UAV Edge-AI system.

The Jetson is intended to perform local video processing and AI inference
close to the UAV system. This allows the planned perception pipeline to
process camera data on the edge rather than depending on a remote
processing system.

The Jetson environment has been prepared as part of the initial platform
setup and hardware familiarisation stage.

## 2. Hardware and Operating Environment

### 2.1 Hardware

- Platform: NVIDIA Jetson Orin Nano Developer Kit
- CPU architecture: ARM64 (aarch64)

### 2.2 Operating System

- Operating System: Ubuntu 22.04
- JetPack: 6.2
- L4T: R36.4.3

The above environment is the current software base used for the Jetson
edge-computing platform.

### 2.3 Development Environment

The Jetson is being prepared as the primary platform for subsequent
video-processing, computer-vision and AI experiments.

The environment includes CUDA support and the software components required
for further edge-AI development.

## 3. Software and Robotics Environment

### 3.1 CUDA

CUDA support has been installed and verified as part of the Jetson
environment.

CUDA provides the GPU-accelerated computing foundation required for
subsequent AI and computer-vision workloads on the Jetson.

### 3.2 ROS 2 Humble

ROS 2 Humble has been installed on the Jetson and basic ROS 2
communication has been verified.

The ROS 2 environment provides the middleware layer for integrating
robotics components, sensors and future perception modules.

### 3.3 Livox MID-360 LiDAR

The Livox MID-360 LiDAR has been connected to the Jetson and made
available through ROS 2.

This provides a foundation for future sensor-based perception and
robotics development alongside the camera-based AI pipeline.

### 3.4 Ollama

Ollama has been installed on the Jetson as part of the local AI
experimentation environment.

It provides a way to run supported AI models locally on the edge
platform and is separate from the planned real-time computer-vision
detection pipeline.

## 4. Environment Verification

The Jetson development environment was verified progressively during the
initial setup.

### 4.1 Platform Verification

The following platform information was verified:

- Jetson Orin Nano Developer Kit
- Ubuntu 22.04
- JetPack 6.2
- L4T R36.4.3
- ARM64 architecture

### 4.2 ROS 2 Verification

Basic ROS 2 communication was tested successfully using ROS 2 publisher
and subscriber nodes.

This confirmed that the ROS 2 environment was functioning correctly on
the Jetson.

### 4.3 Sensor Verification

The Livox MID-360 LiDAR was detected and integrated with the ROS 2
environment.

This confirmed that the Jetson could communicate with the LiDAR through
the configured ROS 2 setup.

### 4.4 AI Environment Verification

The local AI environment was also tested using Ollama and supported
local model experimentation.

Further AI benchmarking and computer-vision performance measurements will
be carried out during the subsequent AI milestones.