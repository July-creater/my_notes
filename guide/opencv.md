# OpenCV 4.10.0

## 安装

1. 安装依赖项

``` bash
sudo apt update
sudo apt upgrade
sudo apt install build-essential cmake pkg-config unzip yasm git checkinstall
sudo apt install libjpeg-dev libpng-dev libtiff-dev
sudo apt install libavcodec-dev libavformat-dev libswscale-dev libavresample-dev
sudo apt install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev
sudo apt install libxvidcore-dev x264 libx264-dev libfaac-dev libmp3lame-dev libtheora-dev
sudo apt install libfaac-dev libmp3lame-dev libvorbis-dev
sudo apt install libopencore-amrnb-dev libopencore-amrwb-dev
sudo apt-get install libdc1394-22 libdc1394-22-dev libxine2-dev libv4l-dev v4l-utils
cd /usr/include/linux
sudo ln -s -f ../libv4l1-videodev.h videodev.h
cd -
sudo apt-get install libgtk-3-dev
sudo apt-get install libtbb-dev
sudo apt-get install libatlas-base-dev gfortran
sudo apt-get install libprotobuf-dev protobuf-compiler
sudo apt-get install libgoogle-glog-dev libgflags-dev
sudo apt-get install libgphoto2-dev libeigen3-dev libhdf5-dev doxygen
sudo apt-get install opencl-headers
sudo apt-get install ocl-icd-libopencl1
```

2. 安装源码，配置cmake选项

``` bash 
cmake -D CMAKE_BUILD_TYPE=RELEASE \
      -D INSTALL_PYTHON_EXAMPLES=OFF \
      -D INSTALL_C_EXAMPLES=OFF \
      -D WITH_TBB=ON \
      -D WITH_CUDA=ON \
      -D BUILD_opencv_cudacodec=OFF \
      -D ENABLE_FAST_MATH=1 \
      -D CUDA_FAST_MATH=1 \
      -D WITH_CUBLAS=1 \
      -D WITH_V4L=OFF \
      -D WITH_LIBV4L=ON \
      -D WITH_QT=OFF \
      -D WITH_GTK=ON \
      -D WITH_GTK_2_X=ON \
      -D WITH_EIGEN=ON
      -D WITH_OPENGL=ON \
      -D WITH_GSTREAMER=ON \
      -D OPENCV_GENERATE_PKGCONFIG=ON \
      -D OPENCV_PC_FILE_NAME=opencv.pc \
      -D OPENCV_ENABLE_NONFREE=ON \
      -D CUDA_nppicom_LIBRARY=stdc++ \
      -D OPENCV_EXTRA_MODULES_PATH=../opencv_contrib-4.6.0/modules \
      -D BUILD_EXAMPLES=OFF ..

```