---
title: "device/save"
slug: "devicesave"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jul 14 2017 14:55:31 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Mar 19 2018 14:52:00 GMT+0000 (Coordinated Universal Time)"
---
Registers or updates a device.

## Request Message

**Authorization**

Access JSON Web Token (RegisterDevice)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "deviceId": {string},
    "device": {
        "name": {string},
        "data": {object},
        "networkId": {integer},
        "deviceTypeId": {integer},
        "isBlocked": {boolean}
    }
}
```

**Message Parameters**

[block:parameters]
{
  "data": {
    "h-0": "Property Name",
    "h-1": "Required",
    "h-2": "Type",
    "h-3": "Description",
    "0-0": "action",
    "0-1": "Yes",
    "0-2": "string",
    "0-3": "Action name: device/save",
    "1-0": "requestId",
    "1-1": "No",
    "1-2": "object",
    "1-3": "Request unique identifier, will be passed back in the response message.",
    "2-0": "deviceId",
    "2-1": "Yes",
    "2-2": "string",
    "2-3": "Device unique identifier.  \nMay contain only letters, digits and dashes.",
    "3-0": "device",
    "3-1": "Yes",
    "3-2": "object",
    "3-3": "A Device resource to register or update.",
    "4-0": "device.name",
    "4-1": "Yes",
    "4-2": "string",
    "4-3": "Device display name.",
    "5-0": "device.data",
    "5-1": "No",
    "5-2": "object",
    "5-3": "Device data, a JSON object with an arbitrary structure.",
    "6-0": "device.networkId",
    "6-1": "Yes",
    "6-2": "integer",
    "6-3": "Associated network id.",
    "7-0": "device.deviceTypeId",
    "7-1": "No",
    "7-2": "integer",
    "7-3": "Associated device type id. Use default device type if it's not defined.",
    "8-0": "device.isBlocked",
    "8-1": "No",
    "8-2": "boolean",
    "8-3": "Indicates whether device is blocked.",
    "9-0": "",
    "9-1": "",
    "9-2": "",
    "9-3": ""
  },
  "cols": 4,
  "rows": 10,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


## Server Message

**Message Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object}
}
```

**Message Parameters**

| Property Name | Type   | Description                                                    |
| :------------ | :----- | :------------------------------------------------------------- |
| action        | string | Action name: device/save                                       |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
