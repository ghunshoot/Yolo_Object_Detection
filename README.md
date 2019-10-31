# Custom object detection using Yolo-v3 in a Linux with GPU or Yolo-v3-tiny in a Jetson Nano

## Index
0. [Introduction](#Introduction)
1. [Requirements](#Requirements)
    * [General Requirements](#General-Requirements)
    * [Requirements for Jetson Nano](#Requirements-for-Jetson-Nano)
    * [Requirements for Linux with GPU](#Requirements-for-Linux-with-GPU)
    * [Requirements for Linux with CPU](#Requirements-for-Linux-with-CPU)
2. [Installation](#Installation)
   * [Installation for Jetson Nano and Linux with GPU](#Installation-for-Jetson-Nano-and-Linux-with-GPU)
   * [Installation for Linux with CPU](#Installation-for-Linux-with-CPU)

## Introduction

## Requirements
### General Requirements
* Ubuntu 18.04
* Python >= 3
* Git = 2.17.1
* OpenCV >= 2.4:
    ```
  $ sudo apt-get install libopencv-dev python-opencv
  $ sudo pip3 install opencv-python
  ```
* Clone this repository.
  ```
  $ git clone https://github.com/ghunshoot/Yolo_Object_Detection.git
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
* [yolov3-tiny_test_CPU.py](https://github.com/ghunshoot/Yolo_Object_Detection/blob/master/yolov3-tiny_test_CPU.py).

## Installation
### Installation for Jetson Nano and Linux with GPU
First we clone darknet.
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

We have to download yolov3-tiny weights.
```
$ cd Yolo_Object_Detection
$ wget https://pjreddie.com/media/files/yolov3-tiny.weights
```
Modify this lines in `yolov3-tiny_test_CPU.py`. `<PATH_TO>` must be replaced with the path of the directory.
```
Line 6: net = cv2.dnn.readNet("<PATH_TO>/darknet/yolov3-tiny.weights", "<PATH_TO>/darknet/cfg/yolov3-tiny.cfg")

Line 8: with open("<PATH_TO>/darknet/cfg/coco.names", "r") as f: classes = [line.strip() for line in f.readlines()]
```
Then we run `yolov3-tiny_test_CPU.py`.
```
$ python3 yolov3-tiny_test_CPU.py
```

## Gathering Data
## Labeling Data
## Training Model
## Inferencing Model



