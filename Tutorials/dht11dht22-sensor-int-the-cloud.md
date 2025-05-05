---
title: "DHT11/DHT22 sensor in the Cloud"
slug: "dht11dht22-sensor-int-the-cloud"
excerpt: "Reading humidity and temperature with cheap and reliable sensor."
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Nov 11 2015 11:56:09 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
One of the most useful case of using IoT is a connecting simple sensors to cloud. But how to connect simple digital sensor to cloud in the most simple way? Definitely we would need  a device which is able to connect to the Internet and the cloud service. Could it be something very cheap and very user friendly at the same time? Connect it easily with DeviceHive!

## Hardware

There are a lot of articles describing this sensors property, protocol  and other technical aspects. No doubt, we would need it if we would be build something big. We would not list it again, be cause it is possible to google it in a seconds. But for the very begging we need to know only that sensor has 3 pins: VDD(power supply, 3.3V can be used), Data and GND. Actual sensor has 4th pin which is not connected to anything and located between Data and GND. So we need power and one line to transmit data on hardware level.
