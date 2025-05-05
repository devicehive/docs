---
title: "devicetype/insert"
slug: "devicetypeinsert"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Jan 11 2018 11:03:27 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jan 11 2018 11:15:39 GMT+0000 (Coordinated Universal Time)"
---
Creates new device type.

## Request Message

**Authorization**

Access JSON Web Token (ManageDeviceType)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "deviceType": {
        "name": {string},
        "description": {string}
    }
}
```

**Message Parameters**

|                        |     |        |                                                                         |
| :--------------------- | :-- | :----- | :---------------------------------------------------------------------- |
| action                 | Yes | string | Action name: devicetype/insert                                          |
| requestId              | No  | object | Request unique identifier, will be passed back in the response message. |
| deviceType             | Yes | object | [DeviceType](doc:devicetype) resource to insert.                        |
| deviceType.name        | No  | string | Device type name.                                                       |
| deviceType.description | No  | string | Device type description.                                                |

## Server Message

**Message Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "deviceType": {
        "id": {int}
    }
}
```

**Message Parameters**

| Property Name | Type   | Description                                                    |
| :------------ | :----- | :------------------------------------------------------------- |
| action        | string | Action name: devicetype/insert                                 |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
| deviceType.id | int    | Device type identifier.                                        |
