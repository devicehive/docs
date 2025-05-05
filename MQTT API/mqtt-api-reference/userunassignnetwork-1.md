---
title: "user/unassignNetwork"
slug: "userunassignnetwork-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 13:00:21 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:31:42 GMT+0000 (Coordinated Universal Time)"
---
Removes association between network and user.

**Authorization**

Access JSON Web Token (ManageUser)

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
    "userId": {long},
    "networkId": {long}
}
```

**Payload Parameters**

| Parameter Name | Required | Type    | Description                                                             |
| :------------- | :------- | :------ | :---------------------------------------------------------------------- |
| action         | Yes      | string  | Action name: user/unassignNetwork                                       |
| requestId      | No       | object  | Request unique identifier, will be passed back in the response message. |
| userId         | Yes      | integer | User identifier                                                         |
| networkId      | Yes      | integer | Network identifier                                                      |

## Response Topic and Payload

**Topic**

```text
dh/response/user/unassignNetwork@{clientId}
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
| action        | string | Action name: user/unassignNetwork                              |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
