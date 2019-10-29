# Object detection using Yolo-v3 with CPU/GPU or Yolo-v3-tiny with a Jetson Nano
Object detection using yolov3-tiny and inference in a Jetson Nano Developer Kit.

## Introduction

## Index
0. [Introduction](#Introduction)
0. [Requirements](#Requirements)

## Requirements
### Requirements for Jetson Nano
* SANDISK micro-SD 64GB 
* Jetson Nano DLI SDK

### Requirements for Linux with GPU
You can check the requirements directly in AlexeyAB/darknet repository https://github.com/AlexeyAB/darknet#requirements.
Anyway here is the most important.
* CMake >= 3.8
    ```
  $ sudo apt-get install cmake
    ```
* CUDA 10.0
* cuDNN >= 7.0 for CUDA 10.0
* OpenCV >= 2.4:

  $ sudo apt-get install libopencv-dev python-opencv
  $ sudo pip3 install opencv-python
  ```

### Requirements for Linux with CPU
* OpenCV >= 2.4:
  ```
  $ sudo apt-get install libopencv-dev python-opencv
  $ sudo pip3 install opencv-python
  ```

## Installation
