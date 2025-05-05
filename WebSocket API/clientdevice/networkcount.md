---
title: "network/count"
slug: "networkcount"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Tue Jan 09 2018 14:47:42 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jan 09 2018 14:50:01 GMT+0000 (Coordinated Universal Time)"
---
Gets count of networks.

## Request Message

**Authorization**

Access JSON Web Token (GetNetwork)

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

| Property name | Required | Type   | Description                                                                    |
| :------------ | :------- | :----- | :----------------------------------------------------------------------------- |
| action        | Yes      | string | Action name: network/count                                                     |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message.        |
| name          | No       | string | Filter by network name.                                                        |
| namePattern   | No       | string | Filter by network name pattern. In pattern wildcards '%' and '\_' can be used. |

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
| action        | string  | Action name: network/count                                     |
| requestId     | object  | Request unique identifier as specified in the request message. |
| status        | string  | Operation execution status (success or error).                 |
| count         | integer | Number of networks that match the filters.                     |
