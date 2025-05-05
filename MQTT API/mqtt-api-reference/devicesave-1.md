---
title: "device/save"
slug: "devicesave-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:55:03 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:27:21 GMT+0000 (Coordinated Universal Time)"
---
Registers or updates a device.

**Authorization**

Access JSON Web Token (RegisterDevice)

## Request Topic and Payload

**Topic**

```text
dh/request
```

**Payload Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "deviceId": {string},
    "device": {
        "name": {string},
        "data": {object},
        "networkId": {integer},
        "isBlocked": {boolean}
    }
}
```

**Payload Parameters**

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
    "7-0": "device.isBlocked",
    "7-1": "No",
    "7-2": "boolean",
    "7-3": "Indicates whether device is blocked.",
    "8-0": "",
    "8-1": "",
    "8-2": "",
    "8-3": ""
  },
  "cols": 4,
  "rows": 9,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


## Response Topic and Payload

**Topic**

```text
dh/response/device/save@{clientId}
```

**Payload Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object}
}
```

**Payload Parameters**

| Property Name | Type   | Description                                                    |
| :------------ | :----- | :------------------------------------------------------------- |
| action        | string | Action name: device/save                                       |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
