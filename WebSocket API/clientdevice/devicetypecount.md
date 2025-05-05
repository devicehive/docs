---
title: "devicetype/count"
slug: "devicetypecount"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Jan 11 2018 10:30:31 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jan 11 2018 10:31:39 GMT+0000 (Coordinated Universal Time)"
---
Gets count of device types the client has access to.

## Request Message

**Authorization**

Access JSON Web Token (GetDeviceType)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "name": {string},
    "namePattern": {string}
}
```

**Message Parameters**

| Property name | Required | Type   | Description                                                                        |
| :------------ | :------- | :----- | :--------------------------------------------------------------------------------- |
| action        | Yes      | string | Action name: devicetype/count                                                      |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message.            |
| name          | No       | string | Filter by device type name.                                                        |
| namePattern   | No       | string | Filter by device type name pattern. In pattern wildcards '%' and '\_' can be used. |

## Server Message

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "status": {string},
    "count": {integer}
}
```

**Message Parameters**

| Property Name | Type    | Description                                                    |
| :------------ | :------ | :------------------------------------------------------------- |
| action        | string  | Action name: devicetype/count                                  |
| requestId     | object  | Request unique identifier as specified in the request message. |
| status        | string  | Operation execution status (success or error).                 |
| count         | integer | Number of device types that match the filters.                 |
