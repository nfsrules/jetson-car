Jetson Autonomous RC Car
========================
Autonomous RC Car using ROS and Keras/TensorFlow. Inspired by JetsonHacks

<p align="center">
<img src="https://github.com/dat-ai/jetson-car/raw/master/docs/img/jetson-car.jpg" width="720">
</p>

Repository Contents
-------------------
* **`/docs`** - research papers, documents, photos related to this project
* **`/model`** - a pre-trained Keras Model file (.json and .h5) to run the car autonomously
* **`/setup`** - Firmwares for Teensy 3.2 & SparkFun IMU Sensor + Set up instructions for Jetson TK1
* **`/src`** - ROS source directory (ROS Nodes and Launch files)
* **`/utils`** - Some unittest files to make sure the car is functional

### System Architecture
-----------------------
<p align="center">
<img src="https://github.com/dat-ai/jetson-car/raw/master/docs/architecture.png" width="640">
</p>

### Goals:
----------
* Get hands-on experience on autonomous vehicle development.
* Understand Deep Learning concepts.
* For Fun ( I probably end up taking the car to some autonomous racing competition. We'll see).

### Dependencies:
-----------------
#### Hardwares: 
* Note: I am working on Bill of Materials. Stay tuned!

1. An RC Car - [RedCat Volcano EPX](https://www.amazon.com/Redcat-Racing-Electric-Volcano-Included/dp/B00HVBVNVG/ref=sr_1_2?ie=UTF8&qid=1487805887&sr=8-2&keywords=RedCat+Volcano+EPX) (stock - no mod) + [Extra battery](https://www.amazon.com/Redcat-Racing-HX-3800MH-B-Battery-7-2V-Connector/dp/B00D2539IU/ref=sr_1_1?ie=UTF8&qid=1487805956&sr=8-1&keywords=Redcat-Racing+HX-3800MH)
2. NVIDIA Jetson TX2
3. Teensy 3.2
4. Intel RealSense R200
5. USB Webcam Logitech C920
6. Razor IMU 9DoF
7. Anker 4-port USB 3.0 Hub
8. RAVPower 23000mAh Power Bank

#### Softwares:

1. Stock OS for Jetson TX2 (JetPack 3.0)
3. ROS Kinetic for ARM (barebone version)
4. Keras using TensorFlow as backend
5. TensorFlow 1.0.1


### Installation Guide: (To be Updated)
----------------------
 
#### Software Setup

 1. Install stock OS using [JetPack 3.0](https://developer.nvidia.com/embedded/jetpack) (Ubuntu 16.04 + CUDA 8.0 + cuDNN v5 + OpenCV4Tegra)
 
 2. Clone this repo:
 ```shell
# Clone the repo
cd ~
git clone https://github.com/dat-ai/jetson-car
```

3. Run setup script to install [ROS Kinetic & Teensy Driver for Jetson TK1](https://github.com/dat-ai/jetson-car/blob/master/setup/tx2_ros_install.sh) - Run this script on TX2.
 
```
# Set up standard ROS workspace
cd jetson-car/src/
catkin_init_make
cd ..
catkin_make
```

 6. Set up ROS environment
```shell
# Add this line to the end of ./.bashrc file
echo "source jetson-car/devel/setup.bash" >> ~/.bashrc
```

#### Hardware Setup

##### 1. Install Teensy Driver
##### 2. Install IMU Razor 9DoF

### Test AutoPilot
------------------

* Open a new terminal
```shell
roscore
```

* Open another new terminal
```shell
roslaunch jetson_joystick jetson_joystick.launch
```

* Activate Autopilot
```shell
cd jetson-car
# Load pre-train model and drive autonomously
python drive.py model/cnn.json
```

### Author(s):
--------------
* [**Dat Nguyen**](https://github.com/dat-ai)
* I am very happy if anyone would like to work with me on this project. please shoot me an email at tdat.nguyen93@gmail.com

### Acknowledgements:
---------------------
* [JetsonHacks](http://www.jetsonhacks.com/) website provides helpful tips and tricks to work with Jetson TK1. JetsonHacks nicely simplifies the installation process with many ready-to-use scripts
* [DuckieTown](http://duckietown.mit.edu), an MIT Course,  is a great place to learn about developing autonomous vehicles.
* UPenn F1/10 Tutorials give a nice introduction to ROS, Hardware installation, and System Architecture for RC Car.
