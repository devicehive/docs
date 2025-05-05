---
title: "Predictive Maintenance"
slug: "predictive-maintenance"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 15 2015 06:14:58 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
COPY: <https://docs.google.com/document/d/1ME98qB3EQ5cTW3RjA6uty8LFWTeNHwVI15GADbYGgTg/edit>

In this tutorial we are going to connect Bluetooth Low Energy (BLE) SensorTag to the DeviceHive cloud using devicehive framework snap cloud and ble modules.  
The case is going to simulate industrial equipment predictive maintenance by measuring vibration level on the equipment and triggering alert if vibration is above the configured threshold.

This will be done using snappy application running on the device. Application uses devicehive framework snap to connect to BLE SensorTags and subscribe to accelerometer sensor readings, readings then decoded and aggregated, variance calculated and sent to cloud as a vibration level.

## 1. Running metrics collection app on the device

Application source code is available on [githuib](https://github.com/devicehive/IoT-framework/blob/master/examples/iot-demo.go)

It is available as compiled snap [here](https://github.com/devicehive/IoT-framework/releases/download/1.0.0-RC1/devicehive-iot-demo_1.0.1_multi.snap)

To install, copy snap file to device and install using command:  
sudo snappy install devicehive-iot-demo_1.0.1_multi.snap  --allow-unauthenticated

Make sure that BLE adapter is available on the device.

## Running server app to monitor vibration levels

At this moment device is configured, connected and ready to send vibration readings to the cloud.  
We are going to use javascript snippet to connect to DeviceHive cloud and receive vibration readings to plot them on chart and trigger BLE lamp if needed.

Sample code is available to play with [here](http://jsbin.com/nilihu/46/edit?html,js,output)

to start, configure your server DH_API and DH_TOKEN. And also DEVICES configuration by overriding values for industrial section. Provide MAC address of your SensorTag and LED lamp (if planning to trigger light on alarm). LEDS config provides association on which LED lamp is to trigger for which SensorTag.

Run the code and choose your snappy device in the dropdown list. It’s name should be the same as was configured in the devicehive cloud config yaml file (see ‘Configuring com.devicehive.cloud agent’ tutorial). click connect and you should see some readings coming to the screen assuming your sensor tag is turned. Connect it to the equipment and monitor the vibration level.
