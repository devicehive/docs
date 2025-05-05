---
title: "devicetype/count"
slug: "devicetypecount-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:55:32 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:27:54 GMT+0000 (Coordinated Universal Time)"
---
Gets count of device types the client has access to.

**Authorization**

Access JSON Web Token (GetDeviceType)

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
    "name": {string},
    "namePattern": {string}
}
```

**Payload Parameters**

| Property name | Required | Type   | Description                                                                        |
| :------------ | :------- | :----- | :--------------------------------------------------------------------------------- |
| action        | Yes      | string | Action name: devicetype/count                                                      |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message.            |
| name          | No       | string | Filter by device type name.                                                        |
| namePattern   | No       | string | Filter by device type name pattern. In pattern wildcards '%' and '\_' can be used. |

## Response Topic and Payload

**Topic**

```text
dh/response/devicetype/count@{clientId}
```

**Payload Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "status": {string},
    "count": {integer}
}
```

**Payload Parameters**

| Property Name | Type    | Description                                                    |
| :------------ | :------ | :------------------------------------------------------------- |
| action        | string  | Action name: devicetype/count                                  |
| requestId     | object  | Request unique identifier as specified in the request message. |
| status        | string  | Operation execution status (success or error).                 |
| count         | integer | Number of device types that match the filters.                 |
