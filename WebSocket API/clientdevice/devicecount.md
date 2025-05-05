---
title: "device/count"
slug: "devicecount"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jan 09 2018 14:27:19 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jan 09 2018 14:40:34 GMT+0000 (Coordinated Universal Time)"
---
Gets count of devices.

## Request Message

**Authorization**

Access JSON Web Token (GetDevice)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "name": {string},
    "namePattern": {string},
    "networkId": {long},
    "networkName": {string}
}
```

**Message Parameters**

| Property name | Required | Type   | Description                                                                   |
| :------------ | :------- | :----- | :---------------------------------------------------------------------------- |
| action        | Yes      | string | Action name: device/count                                                     |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message.       |
| name          | No       | string | Filter by device name.                                                        |
| namePattern   | No       | string | Filter by device name pattern. In pattern wildcards '%' and '\_' can be used. |
| networkId     | No       | long   | Filter by associated network identifier.                                      |
| networkName   | No       | string | Filter by associated network name.                                            |

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
| action        | string  | Action name: device/count                                      |
| requestId     | object  | Request unique identifier as specified in the request message. |
| status        | string  | Operation execution status (success or error).                 |
| count         | integer | Number of devices that match the filters.                      |
