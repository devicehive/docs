---
title: "DS18B20 and ESP8266"
slug: "ds18b20-and-esp8266"
excerpt: ""
hidden: false
metadata:
  image: []
  robots: "index"
createdAt: "Thu Sep 08 2016 11:41:57 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---

One of the most efficient, easy and the cheapest way to connect DS18B20 temperature sensor to cloud service is DeviceHive firmware for ESP8266. This tutorial describes how easily it is possible to do.

## 1. Prepare you ESP8266 chip

Install DeviceHive firmware and configure your DeviceHive server credentials. Follow this [tutorial](chip-in-the-cloud-esp8266#getting-started). If chip was flashed and configured for using with DeviceHive before, there is no need to do it again. Just skip this step then.

## 2. Connect sensor to chip

Connect DS18B20 to your chip as on circuit diagram below:

![](images/23f29b1-circuit.png "circuit.png")

Sensor is powered from the same source as chip. Sesnor output is connected to GPIO0 pin. Resistor is 4.7k Ohm or so. There is no need to use resistor if wires are short because chip also pulls up line. Sample circuit implementation with [Adafruit HUZZAH ESP8266 Breakout board](https://www.adafruit.com/product/2471) and DS18B20 breakout board:

![](images/5521917-sample.jpg "sample.jpg")

## 3. Start cloud client

Download [this html file](https://github.com/devicehive/esp8266-firmware/blob/develop/examples-cloud/ds18b20-onewire.html) (right click on 'Raw' button, 'Save link as...'). Open it in your browser (except Firefox, it has disabled cross domain requests from local file by default) and set up your server credentials:

![](images/4e33d51-web.png "web.png")

Click on 'Run' button and you will get continuously updating temperature data and DS18B20 address as screenshot below:

![](images/3073871-out.png "out.png")

Hardware connectivity is easy with DeviceHive, isn't it? Stay tuned!
