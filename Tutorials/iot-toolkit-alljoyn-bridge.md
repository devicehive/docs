---
title: "IoT Toolkit AllJoyn Bridge"
slug: "iot-toolkit-alljoyn-bridge"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Dec 04 2015 17:48:04 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
# Intro

AllJoyn is an open source software framework that makes it easy for devices and apps to discover and communicate with each other. Developers can write applications for interoperability regardless of transport layer, manufacturer, and without the need for Internet access.  
As many new technologies AllJoyn lacks adoption and specifically availability of IoT devices compatible with AllJoyn protocol. Right now manufacturers have to add custom software and hardware in their devices in order to support AllJoyn. This makes most existing devices incompatible with this new technology.  
One of the elegant solutions is to provide bridge for the existing devices into AllJoyn network. Such bridge was developed as a part of DeviceHive IoT Toolkit and can operate on any Embedded Linux gateway or device.  
It allows to describe any device as an object in AllJoyn network with a simple DSL and add custom logic if necessary on any programming language. As a result, it provides a way to not only add physical devices into AllJoyn network but also any online service or a custom application.

![600](https://files.readme.io/LiPxUgfnTJ6bHPRZFvvQ_alljoyn-bridge.png "alljoyn-bridge.png")

DeviceHive IoT Toolkit AllJoyn bridge supports number of AllJoyn standards out of the box and any new can be implemented by adding more interface implementations. Currently supported:

- About
- Configuration
- Events and Actions 
- Notification
- ControlPanel 
- Lighting Service Framework

# How it Works

As any IoT Toolkit module, the AllJoyn Bridge uses Linux system bus for interoperability with application code. This is very useful as AllJoyn objects definitions are almost identical to Linux dbus definitions. Devices can be described as a set of Objects and Interfaces, that have properties, actions and events. Here’s example of a simplest light bulb description: 

```
        <interface name="org.xyz.SmartHome.Lights">
          <method name="LightsOn">
          </method>
          <method name="LightsOff">            
          </method>
       </interface>
```

Or a power switch with two signals:

```
        <interface name="org.xyz.SmartHome.Switch">
          <signal name="SwitchOn">
            <annotation name="com.devicehive.alljoyn.signal" value="sessionless"/>
          </signal>
          <signal name="SwitchOff">
            <annotation name="com.devicehive.alljoyn.signal" value="sessionless"/>
          </signal>
       </interface>
```

To expose device or an app on AllJoyn network one has simply register it on the dbus using any available library for the language of choice and then call single bridge method. For example 

```
bridge = dbus.Interface(dbus.SystemBus().get_object('com.devicehive.alljoyn.bridge', '/com/devicehive/alljoyn/bridge'), 'com.devicehive.alljoyn.bridge')
bridge.AddService(dbus.service.BusName('org.xyz.SmartHome', dbus.SystemBus()), 'org/xyz/SmartHome/Lights/Bedroom', 'org.xyz.SmartHome.Lights')
```
