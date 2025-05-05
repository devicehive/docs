---
title: "devicetype/update"
slug: "devicetypeupdate"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Jan 11 2018 11:08:53 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jan 11 2018 11:20:03 GMT+0000 (Coordinated Universal Time)"
---
Updates an existing device type.

## Request Message

**Authorization**

Access JSON Web Token (ManageDeviceType)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "deviceTypeId": {string},
    "deviceType": {
        "name": {string},
        "description": {string}
    }
}
```

**Message Parameters**

|                        |     |        |                                                                         |
| :--------------------- | :-- | :----- | :---------------------------------------------------------------------- |
| action                 | Yes | string | Action name: devicetype/update                                          |
| requestId              | No  | object | Request unique identifier, will be passed back in the response message. |
| deviceTypeId           | Yes | string | Device type identifier.                                                 |
| deviceType             | Yes | object | [DeviceType](doc:devicetype) resource for update.                       |
| deviceType.name        | No  | string | Device type name.                                                       |
| deviceType.description | No  | string | Device type description.                                                |

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
| action        | string | Action name: devicetype/update                                 |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
