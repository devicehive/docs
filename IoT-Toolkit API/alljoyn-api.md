---
title: "DeviceHive AllJoyn API"
slug: "alljoyn-api"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Aug 26 2015 16:48:39 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
AllJoyn is a system that allows devices to communicate with other devices around them. A simple example would be a motion sensor letting a light bulb know no one is in the room it is lighting, so it can shut itself off.

## Technology

The system uses the Client–server model to organize itself. For example a light could be a "producer" (server) and a switch a "consumer" (client).

Each "producer" on the network has an XML file called introspection that is used to advertise the devices ability's and what it can be asked to do.

Microsoft has added a technology called Device System Bridge that allows devices using home or building protocols such as Z-Wave and BACnet to appear on an AllJoyn network. 

The system also has technology for audio streaming to multiple device sinks in a synchronized way.

## Quick Start official tutorial

[Here goes ](https://allseenalliance.org/framework/documentation) official guide how to start with AllJoyn devices.

Doesn't it look like a bit complicated? We also agreed with that, so we are happy to present a bit more convenient way to describe AllJoyn devices. With DeviceHive IoT Toolkit :)

## AllJoyn with DeviceHive example

Our mail goal was to simplify AllJoyn device declaration. So, actually we provide interface which describes AllJoyn in declarative way:

```python
class Lamp:
    def __init__(self, mac, name):
        self.Version = 1
        self.mac = mac
        self.name = name        
        self.status = 'DISCOVERED'
        self.LampServiceVersion = 1
        self.LampFaults = []
        self.energyUsage_mW = 15
        self.brigthnessLumen = 100
        self.deviceId = "d7d65f4fbf4ec4c4f1e44da8fe7ca0bc" #8e01a0b4233145c8e35921fdf41dd3bc";
        self.OnOff = False

    def connect(self):
        self.status = 'CONNECTED'
        self._dbus = LampService(self.mac)
        self._config = ConfigService(self.mac, "DeviceHiveVB")
        self._controlpanel = ControlPanelService(self.mac)

        print("Calling alljoyn bridge")

        try:
        # expose to alljoyn             
            bridge = dbus.Interface(bus.get_object(DBUS_BRIDGE_NAME, DBUS_BRIDGE_PATH), dbus_interface='com.devicehive.alljoyn.bridge')
            bridge.AddService(self._dbus.m_service_path, self._dbus.m_service_name, ALLJOYN_LIGHT_PATH, ALLJOYN_LIGHT_NAME, INTROSPECT)
            bridge.AddService(self._config.m_service_path, self._config.m_service_name, ALLJOYN_CONFIG_PATH, ALLJOYN_CONFIG_NAME, CONFIG_INTROSPECT)
            bridge.StartAllJoyn(self._dbus.m_service_name)
            print("%s exposed to Alljoyn" % self.mac)
        except Exception as err:
                print(err)
                traceback.print_exc()
        
    def turnOnOff(self, state):
        self.OnOff = state
        if state:
            print("***LAMP NOW IS ON***")
        else:
            print("***LAMP NOW IS OFF***")

    def destroy(self):
        if self.status == 'CONNECTED':
            self._dbus.deinit()
```

So, we described device class and all what we need to expose this device to AllJoyn network - is to define required services - LampService, ConfigService, AboutService.

[Example shows how to define them.](https://github.com/devicehive/IoT-framework/blob/master/examples/alljoyn/lighting/real-light.py) 

If you would like to build your own AllJoyn connected up with our AllJoyn bridge running, you should create an instance of an AllJoyn bridge object:

```python
bridge = dbus.Interface(bus.get_object(DBUS_BRIDGE_NAME, DBUS_BRIDGE_PATH), dbus_interface='com.devicehive.alljoyn.bridge')
```

Define services you would like to expose:

```python
bridge.AddService(self._dbus.m_service_path, self._dbus.m_service_name, ALLJOYN_LIGHT_PATH, ALLJOYN_LIGHT_NAME, INTROSPECT)
```

And start the service, which would essentially bridge AllJoyn messages to your client application:

```python
bridge.StartAllJoyn(self._dbus.m_service_name)
```

[Find more details on the github.](https://github.com/devicehive/IoT-framework/blob/master/examples/alljoyn/lighting/real-light.py)
