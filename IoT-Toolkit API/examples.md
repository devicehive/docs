---
title: "Examples - draft"
slug: "examples"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Aug 26 2015 17:58:33 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
All examples could be downloaded [here](https://github.com/devicehive/IoT-framework/tree/master/examples).

These are examples of usage IoT framework. To run each of them you have to install IoT framework on target machine. You may use this examples to find out how to use components of IoT ferameowork. For running each of this examples you will need to upload it to target machine and run there for Python examples. For go example you will need to compile them before.

## cloud.py

Simple application which uses cloud part of IoT framework. It replyes with echoes on each sended from cloud commands. Usage: run it, send command and check result of command. It should be the same.

## cpu-stats.go

Simple application which reads current system state(CPU, momory usage) and sends it to cloud with some period of time. Usage: run this demo and check DeviceHive server, it should recieve notifications with current machine status.

## dash-xylo.go

Simple application that sends some melody for playback to Play-I robot. These robots uses BLE for connectivity purpose and they have special characterstic which can be written and robot will playback recorder data.

## heart-pulse-demo.go

TODO

## iot-demo.go

TODO

## lamp.py

Simple application which uses bluetooth low energy part of IoT Framework. It scans for BLE bulb with name DELIGHT and since it found send command to turn on or off. Usage: uncomment action that you need to perform at line 22-23 and run this demo.  
pod.py

TODO

## sensortag.py

Simple application which shows how to connect to TI SensorTag. It connects to it, enable accelerometer, receives notification with accelerometer data and prints it to std output. Usage: run this demo on machine with BLE, turn on TI Sensor tag in BLE radius and demo will print accelerometer data from it.
