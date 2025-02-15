# NanoDet NCNN Demo

This project provides NanoDet image inference, webcam inference and benchmark using
[Tencent's NCNN framework](https://github.com/Tencent/ncnn).

# How to build

## Windows
### Step1.
Download and Install Visual Studio from https://visualstudio.microsoft.com/vs/community/

### Step2.
Download and install OpenCV from https://github.com/opencv/opencv/releases

### Step3(Optional).
Download and install Vulkan SDK from https://vulkan.lunarg.com/sdk/home

### Step4.
Clone NCNN repository

``` shell script
git clone --recursive https://github.com/nihui/ncnn.git 
```
Build NCNN following this tutorial: [Build for Windows x64 using VS2017](https://github.com/Tencent/ncnn/wiki/how-to-build#build-for-windows-x64-using-visual-studio-community-2017)

### Step5.

Modify CMakeLists.txt to your environment settings.

Build project

Open x64 Native Tools Command Prompt for VS 2019 or 2017

``` cmd
cd <this-folder>
mkdir -p build
cd build
cmake ..
msbuild nanodet_demo.vcxproj /p:configuration=release /p:platform=x64
```

## Linux

### Step1.
Build and install OpenCV from https://github.com/opencv/opencv

### Step2(Optional).
Download Vulkan SDK from https://vulkan.lunarg.com/sdk/home

### Step3.
Clone NCNN repository

``` shell script
git clone --recursive https://github.com/nihui/ncnn.git 
```

Build NCNN following this tutorial: [Build for Linux / NVIDIA Jetson / Raspberry Pi](https://github.com/Tencent/ncnn/wiki/how-to-build#build-for-linux)

### Step4.

Modify CMakeLists.txt to your environment settings.

Build project

``` shell script
cd <this-folder>
mkdir build
cd build
cmake ..
make
```

# Run demo

Download NanoDet ncnn model.

Copy nanodet_m.param and nanodet_m.bin to demo program folder.

## Webcam

```shell script
nanodet_demo 0 0
```

## Inference images

```shell script
nanodet_demo 1 IMAGE_FOLDER/*.jpg
```

## Inference video

```shell script
nanodet_demo 2 VIDEO_PATH
```

## Benchmark

```shell script
nanodet_demo 3 0
```
![bench_mark](benchmark.jpg)
****

Notice:

If benchmark speed is slow, try to limit omp thread num.

Linux:

```shell script
export OMP_THREAD_LIMIT=4
```
