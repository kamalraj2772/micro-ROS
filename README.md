ROS 2 + micro-ROS:
Jetson Orin Nano, ZED2i, and ESP32 Integration

This repository documents my work integrating ROS 2 with micro-ROS, connecting a Jetson Orin Nano, a ZED2i stereo camera, and multiple ESP32 microcontrollers to build a distributed robotic system. The setup enables real-time data publishing and subscribing between edge AI devices and embedded systems.

Project Overview
Goals:

◇ Use the ZED2i camera on Jetson Orin Nano to compute angle and velocity data.
◇ Publish this data from Jetson using a ROS 2 node.
◇ Subscribe to the data on the ESP32 using micro-ROS and take action accordingly.
◇ Display received data on a 16x2 I2C LCD and over Serial1.
◇ Use a second ESP32 node to control motors (e.g., Neo V1.1 with encoders) based on received commands.


---------------------------------------

System Architecture;
Jetson Orin Nano
ROS 2 Humble
Custom node (zed2i_publish) reads data from ZED2i and publishes:
angle (float)
velocity (float)

Topics:
/zed2i/angle
/zed2i/velocity
ESP32 (micro-ROS client)
micro-ROS Arduino library

Subscribes to:
/zed2i/angle → Controls motor to desired angle
/zed2i/velocity → For motion profiling


Displays values on:
16x2 LCD via I2C
