# Welcome

Our __wearable motion capture system__ provides arm-pose estimations from a single smartwatch. This allows motion capture of the human arm anytime and anywhere. Our system comprises apps to stream sensor data from wearable devices, a python package to estimate arm poses from streamed sensor data, and an optional 3D visualization using Unity.

:iphone::watch: :computer: Please visit [__this website__](https://faweigend.com/research/wearable-motion-capture/) for videos and more material.

:chart_with_upwards_trend: Model training and test data is available on [__Hugging Face__](https://huggingface.co/datasets/faweigend/wearmocap).

:book: The most-recently published [__technical report__](https://www.frontiersin.org/journals/robotics-and-ai/articles/10.3389/frobt.2024.1478016/full).

:tv: Our most-recent [__video__](https://www.youtube.com/watch?v=hyQY5dyWPLU&t=4s).


# Quick Start Guide

For more detailed instructions and advanced modes please see our [wiki](https://github.com/wearable-motion-capture/.github/wiki). As shown below, this framework features three modes. **Watch Only** estimates arm poses from the data of a single smartwatch. **+Phone Upper Arm** enables our most accurate arm pose predictions. **+Phone Pocket** allows to move around and change body orientation. The quick start guide gets you started with the **Watch Only** mode.

<p align="center">
  <img src="https://github.com/wearable-motion-capture/.github/blob/main/profile/httpdocs/modes.gif" alt="Modes"/>
</p>

### The Modules and Pipeline

Our __wearable motion capture system__ is composed of modules. 
Each of these modules is one repository in this GitHub Organization.
Namely, they are:

* [__sensor-stream-apps__](https://github.com/wearable-motion-capture/sensor-stream-apps) provides the apps to stream sensor readings from wearable devices to a remote machine.
* [__arm-pose-estimation__](https://github.com/wearable-motion-capture/arm-pose-estimation) opens sockets to receive streamed data from wearable devices and processes them into arm posture estimations.
* [__arm-pose-visualization__](https://github.com/wearable-motion-capture/arm-pose-visualization) visualizes arm posture estimations in real time using a 3D avatar.

The figure below summarizes the data stream from smart devices to visualization. The individual components are connected through UDP streams, but Arm Pose Estimation and Arm Pose Visualization can run on the same machine. The UDP streaming from smart devices to the Arm Pose Estimation requires a local WiFi connection.

<p align="center">
  <img src="https://github.com/wearable-motion-capture/.github/blob/main/profile/httpdocs/modules.jpg" alt="Modules"/>
</p>

### Basic Installs

First, install our [__sensor-stream-apps__](https://github.com/wearable-motion-capture/sensor-stream-apps) with Android Studio. 
Your smartwatch has to be in developer mode and has to be connected the same WiFi as the machine that you want to run arm pose estimations on. 
If you are unfamiliar with installing an app in developer mode, we recommend following the step-by-step instructions in 
our [extensive wiki](https://github.com/wearable-motion-capture/.github/wiki).

Then, clone [__arm-pose-estimation__](https://github.com/wearable-motion-capture/arm-pose-estimation) and install it with pip:
```
pip3 install /path/to/cloned/repository
```
For streaming data from the watch only, copy the [watch_only.py](https://github.com/wearable-motion-capture/arm-pose-estimation/blob/main/example_scripts/stream/watch_only.py) from the [example_scripts](https://github.com/wearable-motion-capture/arm-pose-estimation/tree/main/example_scripts) directory.
Run the script with your local IP as a parameter. For example:
```
python3 watch_only.py 192.168.1.123
```

Finally, to visualize arm pose estimates, you can either download a build of the visualizer tool [here](https://drive.google.com/drive/folders/18LDbT_E33oyWSd0J2E86wi2IfsF00x9S?usp=sharing), or you clone our [__arm-pose-visualization__](https://github.com/wearable-motion-capture/arm-pose-visualization) repository and open it in Unity.
Please also see our [wiki](https://github.com/wearable-motion-capture/.github/wiki) if you want to use Unity.
