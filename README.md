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
* CMake >= 3.8:
    ```
  $ sudo apt-get install cmake
    ```
* CUDA 10.0
* cuDNN >= 7.0 for CUDA 10.0
* OpenCV >= 2.4:
    ```
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
### Installation for Jetson Nano
First we download darknet, we need to have git installed.
```
$ git clone https://github.com/AlexeyAB/darknet
$ cd darknet
$ git checkout darknet_yolo_v3 -b jetson_nano
```
Modify the Makefil in ~/darknet
```
GPU=1
CUDNN=1
OPENCV=1
ARCH= -gencode arch=compute_53,code=[sm_53,compute_53]
``` 
```
~/darknet
$ git clone https://github.com/AlexeyAB/darknet
```
$ cd ~/github/darknet
$ wget https://pjreddie.com/media/files/yolov3.weights
$ wget https://pjreddie.com/media/files/yolov3-tiny.weights
### Installation for Linux with GPU
### Installation for Linux with CPU

