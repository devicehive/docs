---
title: "DeviceHive BLE (Bluetooth low energy) API"
slug: "devicehive-ble-bluetooth-low-energy-api"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Aug 26 2015 16:49:40 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
We use <https://github.com/devicehive/gatt> for communication with devices.

## API methods

**Connect(mac, random)**  
@param mac (string) - device MAC address  
@param random (bool) - Bluetooth Address type (true for random, false for static)  
@return bool 

Function tries to find device in the discovered devices list. If it is absent there, we grab device info through gatttool using provided MAC address and Bluetooth address type value. Once found, we add new device structure into discovered devices list.  
Then function tries to establish connection with device during 3-5s. Returns true in case connection established, false with error otherwise.

**Connected(mac)**  
@param mac (string) - MAC address  
@return bool  
Check if connection to device is established.

**Disconnect(mac)**  
@param mac (string) - MAC address  
@return nil

Function validates whether device present in the discovered devices list and cancels connection in that case. Otherwise returns error.

**ScanStart()**  
@return nil or error

If HCI is connected, function tries to find new devices. Once device is found, PeripheralDiscovered signal will be fired.  
If HCI is not connected, or connection is in progress, an error will be returned.

**ScanStop()**  
@return nil or error

If HCI is not connected, error will be returned. Otherwise scan stop occurs.

The difference between Gatt Indications and Gatt Notifications was perfectly explained by Håkon Alseth from Nordic Semiconductor:

```
They are basically the same thing, just with a small twist to it.

On each Indication, you must then do a application level ACK to say that this is the data I need. Basically like this: "here you have a packet. Is this something you want to acknowledge?"

On each notification, you only get an event saying "you have received a packet, here it is"

Indications are slower as you only can send one indication per connection interval (your application ACK will be sent on the next connection interval).

Notifications are preferred if you need a higher transfer rate. Using notifications, you are allowed to queue a certain number of packets before sending, and once the buffer is full, you get a NO_TX_BUFFERS error back from sd_ble_gatts_hvx(). When a packet has been sent over the link layer, you'll get a BLE_EVT_TX_COMPLETE event, at which point you can queue further packets.
```

**GattIndications(mac, uuid, enable)**  
@param mac (string) - MAC address  
@param uuid (string)  
@param enable (bool)

If enable is true, IndicationReceived signal will be emitted, and SetIndicateValue will set indications for the value of a specified characteristic.  
If enable is false, SetIndicateValue will set value as nil.

** GattNotifications(mac, uuid, enable)**  
@param mac (string) - MAC address  
@param uuid (string) - device characteristic uuid  
@param enable (bool)

If enable is true, IndicationReceived signal will be emitted, and SetNotifyValue will set notifications for the value of a specified characteristic.  
If enable is false, SetNotifyValuewill set value as nil.

** GattRead(mac, uuid)**  
@param mac (string) - MAC address  
@param uuid (string) - device characteristic uuid

Read characteristic with specified uuid from MAC address.

** GattWrite(mac, uuid, message)**  
@param mac (string) - MAC address  
@param uuid (string) - device characteristic uuid  
@param message (string)

Write "message" value for characteristic with specified uuid for MAC address. Operation response will be returned

```
const (
	attEcodeSuccess           attEcode = 0x00 // Success
	attEcodeInvalidHandle     attEcode = 0x01 // The attribute handle given was not valid on this server.
	attEcodeReadNotPerm       attEcode = 0x02 // The attribute cannot be read.
	attEcodeWriteNotPerm      attEcode = 0x03 // The attribute cannot be written.
	attEcodeInvalidPDU        attEcode = 0x04 // The attribute PDU was invalid.
	attEcodeAuthentication    attEcode = 0x05 // The attribute requires authentication before it can be read or written.
	attEcodeReqNotSupp        attEcode = 0x06 // Attribute server does not support the request received from the client.
	attEcodeInvalidOffset     attEcode = 0x07 // Offset specified was past the end of the attribute.
	attEcodeAuthorization     attEcode = 0x08 // The attribute requires authorization before it can be read or written.
	attEcodePrepQueueFull     attEcode = 0x09 // Too many prepare writes have been queued.
	attEcodeAttrNotFound      attEcode = 0x0a // No attribute found within the given attribute handle range.
	attEcodeAttrNotLong       attEcode = 0x0b // The attribute cannot be read or written using the Read Blob Request.
	attEcodeInsuffEncrKeySize attEcode = 0x0c // The Encryption Key Size used for encrypting this link is insufficient.
	attEcodeInvalAttrValueLen attEcode = 0x0d // The attribute value length is invalid for the operation.
	attEcodeUnlikely          attEcode = 0x0e // The attribute request that was requested has encountered an error that was unlikely, and therefore could not be completed as requested.
	attEcodeInsuffEnc         attEcode = 0x0f // The attribute requires encryption before it can be read or written.
	attEcodeUnsuppGrpType     attEcode = 0x10 // The attribute type is not a supported grouping attribute as defined by a higher layer specification.
	attEcodeInsuffResources   attEcode = 0x11 // Insufficient Resources to complete the request.
)

```

** GattWriteNoResp(mac, uuid, message)**  
@param mac (string) - MAC address  
@param uuid (string)  
@param message (string)

the same as above, but without response

**OnInit(device, state)**  
@param device (gatt.Device)  
@param state (gatt.State)

Function changes bus object connected field to true or false depending on state value.

** OnPeripheralConnected(p, err) **  
@param p (gatt.Peripheral)  
@param err (error)

Function adds Peripheral to connected devices list.

** OnPeripheralDisconnected(p, err) **  
@param p (gatt.Peripheral)  
@param err (error)

Function deletes Peripheral from discovered devices list if present there,  
Then if Peripheral exists in connected devices list, we delete it from there and emit PeripheralDisconnected signal.

** OnPeripheralDiscovered(p, a, rssi) **  
@param p (gatt.Peripheral)  
@param a (gatt.Advertisement)  
@param rssi (int)

Function emits PeripheralDiscovered signal for specified Peripheral and rssi

Sample GATT client in Python:

```python
#!/usr/bin/env python

import dbus
from dbus.mainloop.glib import DBusGMainLoop
from gi.repository import GObject
import array

DBusGMainLoop(set_as_default=True)

def get_ble():
    return dbus.Interface(dbus.SystemBus().get_object("com.devicehive.bluetooth", '/com/devicehive/bluetooth'), "com.devicehive.bluetooth")

ble = get_ble()
def device_discovered(mac, name, rssi):
    if (name == 'DELIGHT'):
        ble.ScanStop()
        ble.Connect(mac)

def device_connected(mac):
    print "Connected to %s" % (mac)
    ble.GattWrite(mac, "fff1", "0f0d0300ffffffc800c800c8000059ffff")

def main():
    ble.ScanStart()
    ble.connect_to_signal("DeviceDiscovered", device_discovered)
    ble.connect_to_signal("DeviceConnected", device_connected)

    GObject.MainLoop().run()

if __name__ == '__main__':
    main()
```
