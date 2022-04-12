# install-pytorch-from-source


### Why install from source?
Majority of the time, we don't need to build Pytorch from source. However, there are cases when it is necessary:
  + We need pytorch support the latest CUDA version
  + Accompanying libraries such as torchvision requires pytorch to be built from sources.

### Step by step instruction

#### Step1: install Nvidia-drivers
This is the main source for guidance:
```
https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html
```

We can either install package using command lines:
```
https://developer.nvidia.com/cuda-downloads
```
or download standalone packages, which are called drivers:
```
https://www.nvidia.com/Download/driverResults.aspx/187162/en-us
```
NOTE: because of the way they name the same thing in two different ways, CUDA drivers v.s CUDA packages, it may be confusing. In fact, we can only choose one of these.

NOTE2: if typing nvidia-smi and you encounter an error, try to reboot the computer first, if the error persist, try typing `dmesg`, and check the log:
```
$ dmesg|grep -i nvrm -A3
[  113.647054] NVRM: API mismatch: the client has the version 510.54, but
               NVRM: this kernel module has the version 510.47...
```
Then, we must use the driver. Download the driver directly from NVIDIA with the version match or greater than the client version.

#### Step2: install Pytorch from source
Visit this website and following the instruction:
```
https://github.com/pytorch/pytorch
```
If there is an error and previously driver is used for installing CUDA, we must add specify CUDA filepath for Pytorch:
```
export PATH=/usr/local/cuda-11.6/bin${PATH:+:${PATH}}
```
The easiest way to detect this error is to type `nvcc`, if this command is not recognized, we will have problems installing Pytorch from source.

#### Step3: install Torchvision
Following instruction from this website:
```
https://github.com/pytorch/vision
```
