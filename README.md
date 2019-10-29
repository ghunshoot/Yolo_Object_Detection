# Object detection using Yolo-v3 in a Linux with GPU or Yolo-v3-tiny in a Jetson Nano/Linux with CPU
Object detection using yolov3-tiny and inference in a Jetson Nano Developer Kit.

## Introduction

## Index
0. [Introduction](#Introduction)
1. [Requirements](#Requirements)
    * [Requirements for Jetson Nano](#Requirements_for_Jetson_Nano)
    * [Requirements for Linux with GPU](#Requirements_for_Linux_with_GPU)
    * [Requirements for Linux with CPU](#Requirements_for_Linux_with_CPU)
2. [Installation](#Installation)
   * [Installation for Jetson Nano and Linux with GPU](#Installation_for_Jetson_Nano_and_Linux_with_GPU)

## Requirements
### General Requirements
* Python >= 3
* Git = 2.17.1
* OpenCV >= 2.4:
    ```
  $ sudo apt-get install libopencv-dev python-opencv
  $ sudo pip3 install opencv-python
  ```

### Requirements for Jetson Nano
The NVIDIA Deep Learning Institute have a course that you must take to install and demo de Jetson Nano. This SDK brings all the necesary packages and libraries. Also you can earn a certificate for free. Check the course https://courses.nvidia.com/courses/course-v1:DLI+C-RX-02+V1/about. 
* AC/DC converter minimum 3A.
* SANDISK micro-SD 64GB (tested with ADATA micro-SD and didn't run the OS).
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

### Requirements for Linux with CPU
* OpenCV >= 2.4
* [yolov3-tiny_test_CPU.py](https://github.com/ghunshoot/Yolo_Object_Detection/blob/master/yolov3-tiny_test_CPU.py).

## Installation
### Installation for Jetson Nano and Linux with GPU
First we download darknet, we need to have git installed.
```
$ git clone https://github.com/AlexeyAB/darknet
$ cd darknet
```
Additional command only for the Jetson Nano.
```
$ git checkout darknet_yolo_v3 -b jetson_nano
```
Modify the Makefile in ~/darknet.
```
GPU=1
CUDNN=1
OPENCV=1
```
For Jetson Nano:
```
ARCH= -gencode arch=compute_53,code=[sm_53,compute_53]
``` 
For Linux with GPU:
```
ARCH= # Here we add the corresponding ARCH to your GPU model. This are are commented below this line.
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
# Yolo-v3
$ ./darknet detect cfg/yolov3.cfg yolov3.weights data/dog.jpg

# Yolo-v3-tiny
$ ./darknet detect cfg/yolov3-tiny.cfg yolov3-tiny.weights data/dog.jpg
```

### Installation for Linux with CPU
Running Yolo-v3-tiny can be achieved only using OpenCV.
We download darknet and weights, we need to have git installed.
```
$ git clone https://github.com/AlexeyAB/darknet
$ cd darknet
$ wget https://pjreddie.com/media/files/yolov3-tiny.weights
```
Then we run `yolov3-tiny_test_CPU.py`.
```
$ python3 yolov3-tiny_test_CPU.py
```


