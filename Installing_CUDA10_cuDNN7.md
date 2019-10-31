# Installation of CUDA and cudnn7

[CUDA Toolkit 10.0 Archive](https://developer.nvidia.com/cuda-10.0-download-archive?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1604&target_type=debnetwork)

$ sudo dpkg -i cuda-repo-ubuntu1604_10.0.130-1_amd64.deb
$ sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/7fa2af80.pub

$ sudo apt-get update

$ sudo apt-get install cuda


[cuDNN Download](https://developer.nvidia.com/rdp/cudnn-download)

cuDNN Library for Linux

$ tar -xzvf <cudnn_name_package>

$ sudo cp cuda/include/cudnn.h /usr/local/cuda/include

$ sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64

$ sudo chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn*
