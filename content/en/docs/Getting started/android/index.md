---
title: "Getting Started with DaisyKit Android"
linkTitle: "DaisyKit Android"
weight: 3
description: >
  Compile and Run DaisyKit Android
---

DaisyKit Android is built on top of [DaisyKit SDK](/docs/getting-started/sdk/). It contains wrapper code, examples to use DaisyKit in Android mobile devices.

**Github:** <https://github.com/VNOpenAI/daisykit-android>.

![DaisyKit Architecture](daisykit-architecture.png)

## I. Build and Run

**Dependencies:** Android NDK 21.3, CMake 3.10.2.

### Step 1: Clone the source code

```
git clone --recurse-submodules https://github.com/VNOpenAI/daisykit-android.git
```

Or 

```
git clone https://github.com/VNOpenAI/daisykit-android.git
cd daisykit-android
git submodule update --init
```
### Step 2: Download NCNN

https://github.com/Tencent/ncnn/releases

- Download ncnn-YYYYMMDD-android-vulkan.zip or build ncnn for android yourself
- Extract ncnn-YYYYMMDD-android-vulkan.zip into **app/src/main/jni** and change the **ncnn_DIR** path to yours in **app/src/main/jni/CMakeLists.txt**

### Step 3: Download OpenCV

https://github.com/nihui/opencv-mobile

- Download opencv-mobile-XYZ-android.zip
- Extract opencv-mobile-XYZ-android.zip into **app/src/main/jni** and change the **OpenCV_DIR** path to yours in **app/src/main/jni/CMakeLists.txt**

### Step 4: Download assets

- Download all assets [here](https://drive.google.com/drive/folders/1ZAM8W4hHkV7-zmfHFjIGLAuso3QajUfW?usp=sharing) and put into `app/src/main/assets/` folder.

### Step 5: Build

- Open this project with Android Studio, build it and enjoy!

## II. Some notes

- Android ndk camera is used for best efficiency.
- Crash may happen on very old devices for lacking HAL3 camera interface.
- All models are manually modified to accept dynamic input shape.
- Most small models run slower on GPU than on CPU, this is common.
- FPS may be lower in dark environment because of longer camera exposure time.

## III. Errors and Fixes

### 1. Errors because of build tool version

```
No toolchains found in the NDK toolchains folder for ABI with prefix: arm-linux-androideabi
```

```
clang ++: error: unknown argument: '-static-openmp'
```

**How to fix?** Install NDK 21.3, CMake 3.10.2.

### 2. Crashing app

Check if you have downloaded and extracted all assets. See into assets folder at `app/src/main/assets`. There should be 3 subfolders here: `models`, `configs`, and `images`.