# Deepstream 5.1 Centerface App

This Deepstream application showcases Centerface running at high FPS throughput!

[![FPS](resources/centerface.gif)](https://www.linkedin.com/posts/akashjames_facedetection-computervision-gpu-activity-6803721379087818752-yYz4)

P.S - Click the gif to watch the entire video!

## Index

1. [Deepstream Setup](#Deepstream-Setup)
    1. [Install System Dependencies](#Install-System-Dependencies)
    2. [Install Deepstream](#Install-Deepstream)
2. [Running the Application](#Running-the-Application)
    1. [Clone the repository](#Cloning-the-repository)
    2. [Download the weights file](#download-the-weights-file)
    3. [Build the application](#build-the-application)
    4. [Run with different input sources](#Run-with-different-input-sources)
3. [Citations](#citations)

## Deepstream Setup

This post assumes you have a fully functional Jetson device. If not, you can refer the documentation [here](https://docs.nvidia.com/jetson/jetpack/install-jetpack/index.html).

### 1. Install System Dependencies

```sh
sudo apt install \
libssl1.0.0 \
libgstreamer1.0-0 \
gstreamer1.0-tools \
gstreamer1.0-plugins-good \
gstreamer1.0-plugins-bad \
gstreamer1.0-plugins-ugly \
gstreamer1.0-libav \
libgstrtspserver-1.0-0 \
libjansson4=2.11-1
```

### 2. Install Deepstream

Download the DeepStream 5.1 Jetson Debian package `deepstream-5.1_5.1.0-1_arm64.deb`, to the Jetson device from [here](https://developer.nvidia.com/deepstream-getting-started). Then enter the command:

```sh
sudo apt install deepstream-5.1_5.1.0-1_arm64.deb
```

For more information, go to the get started page of Deepstream [here](https://docs.nvidia.com/metropolis/deepstream/dev-guide/index.html).

## Running the Application

### 1. Clone the repository

This is a straightforward step, however, if you are new to git, I recommend glancing threw the steps.

First, install git

```sh
sudo apt install git
```

Next, clone the repository

```sh
# Using HTTPS
https://github.com/aj-ames/Centerface-Deepstream.git
# Using SSH
git@github.com:aj-ames/Centerface-Deepstream.git
```

### 2. Download the weights file

Download the weights file from google-drive and place it in `models/Centerface` directory.

* [Centerface 1280x736](https://drive.google.com/file/d/1n5o_uJlinJ6FNv9r8FKSo2MpA9B1UNpG/view?usp=sharing)
* [Centerface 960x544]([google-drive](https://drive.google.com/file/d/1znEKZV4-XXSgCP6_7qYIeFDHjAslo1sa/view?usp=sharing))

### 3. Build the application

First, build the application by running the following command:

```sh
make clean && make -j$(nproc)
```

This will generate the binary called `ds-centerface`. This is a one-time step and you need to do this only when you make source-code changes.

### 4. Run with different input sources

Next, create a file called `inputsources.txt` and paste the path of videos or rtsp url.

```sh
file:///home/astr1x/Videos/sample.mp4
rtsp://admin:admin%40123@192.168.1.1:554/stream
```

Now, run the application by running the following command:

```sh
./ds-centerface
```

## Citations

* [AlexeyAB/darknet](https://github.com/AlexeyAB/darknet)