---
title: "devicetype/list"
slug: "devicetypelist"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Jan 11 2018 10:11:18 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jan 11 2018 10:47:19 GMT+0000 (Coordinated Universal Time)"
---
Gets list of device types.

The result list is limited to device types the client has access to.

## Request Message

**Authorization**

Access JSON Web Token (GetDeviceType)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "name": {string},
    "namePattern": {string},
    "sortField": {string},
    "sortOrder": {string},
    "take": {integer},
    "skip": {integer}
}
```

**Message Parameters**

| Property name | Required | Type    | Description                                                                        |
| :------------ | :------- | :------ | :--------------------------------------------------------------------------------- |
| action        | Yes      | string  | Action name: devicetype/list                                                       |
| requestId     | No       | object  | Request unique identifier, will be passed back in the response message.            |
| name          | No       | string  | Filter by device type name.                                                        |
| namePattern   | No       | string  | Filter by device type name pattern. In pattern wildcards '%' and '\_' can be used. |
| sortField     | No       | string  | Result list sort field. Available values are ID and Name.                          |
| sortOrder     | No       | string  | Result list sort order. Available values are ASC and DESC.                         |
| take          | No       | integer | Number of records to take from the result list.                                    |
| skip          | No       | integer | Number of records to skip from the result list.                                    |

## Server Message

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "status": {string},
    "deviceTypes": [{
        "id": {string},
        "name": {string},
        "description": {string}
    }]
}
```

**Message Parameters**

| Property Name          | Type   | Description                                                                    |
| :--------------------- | :----- | :----------------------------------------------------------------------------- |
| action                 | string | Action name: devicetype/list                                                   |
| requestId              | object | Request unique identifier as specified in the request message.                 |
| status                 | string | Operation execution status (success or error).                                 |
| deviceTypes            | array  | The array of device types.                                                     |
| deviceType             | object | The [DeviceType](doc:devicetype) resource representing the type of the device. |
| deviceType.id          | string | Device type identifier.                                                        |
| deviceType.name        | string | Device type name.                                                              |
| deviceType.description | string | Device type description.                                                       |
