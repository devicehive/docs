---
title: "DeviceHive EnOcean API"
slug: "devicehive-enocean-api"
excerpt: "EnOcean daemon for dbus."
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Aug 26 2015 16:51:06 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
All EnOcean actuators harvest energy from environment and use it to send short message via air to reciver that connect to machine with this framework. This message can be obtain with:

message_received

dbus signal of this framework. So, usage is extremely simple:

```text
enocean_manager = bus.get_object(DBUS_BUS_ENOCEAN_NAME, '/com/devicehive/enocean')
enocean = dbus.Interface(enocean_manager, DBUS_BUS_ENOCEAN_NAME)
enocean.connect_to_signal('message_received', message_received)
```

just unparse pure data in **message_received **callback and use it.

## Running

Current daemon has dependency on enocean python3 library:

```text
pip3 install enocean
```
