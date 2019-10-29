# Object detection using Yolo-v3 with CPU/GPU or Yolo-v3-tiny with a Jetson Nano
Object detection using yolov3-tiny and inference in a Jetson Nano Developer Kit.

## Introduction

## Index
0. [Introduction](#Introduction)
0. [Requirements](#Requirements)

## Requirements
### Requirements for Jetson Nano
The NVIDIA Deep Learning Institute have a course that you must take to install and demo de Jetson Nano. This SDK brings all the necesary packages and libraries. Also you can earn a certificate for free. Check the course https://courses.nvidia.com/courses/course-v1:DLI+C-RX-02+V1/about. 
* AC/DC converter minimum 3A.
* SANDISK micro-SD 64GB (test with ADATA micro-SD and didn't run the OS).
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
Modify the Makefile in ~/darknet.
```
GPU=1
CUDNN=1
OPENCV=1
ARCH= -gencode arch=compute_53,code=[sm_53,compute_53]
``` 
Then we run make.
```
$ cd darknet
$ make
```
Install the weights for Yolo-v3 and Yolo-v3-tiny.
```
$ wget https://pjreddie.com/media/files/yolov3.weights
$ wget https://pjreddie.com/media/files/yolov3-tiny.weights
```
To test installation, run this command.
```
$ ./darknet detect cfg/yolov3.cfg yolov3.weights data/dog.jpg
```
### Installation for Linux with GPU
### Installation for Linux with CPU

