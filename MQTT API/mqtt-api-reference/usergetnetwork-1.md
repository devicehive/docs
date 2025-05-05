---
title: "user/getNetwork"
slug: "usergetnetwork-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:59:25 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:31:23 GMT+0000 (Coordinated Universal Time)"
---
Gets information about user/network association.

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
    "userId": {integer},
    "networkId": {integer}
}
```

**Payload Parameters**

| Parameter Name | Required | Type    | Description                                                             |
| :------------- | :------- | :------ | :---------------------------------------------------------------------- |
| action         | Yes      | string  | Action name: user/getNetwork                                            |
| requestId      | No       | object  | Request unique identifier, will be passed back in the response message. |
| userId         | Yes      | integer | User identifier                                                         |
| networkId      | Yes      | integer | Network identifier                                                      |

## Response Topic and Payload

**Topic**

```text
dh/response/user/getNetwork@{clientId}
```

**Payload Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "network": {
        "id": {int},
        "name": {string},
        "description": {string}
    }
}
```

**Payload Parameters**

| Property Name       | Type    | Description                                                    |
| :------------------ | :------ | :------------------------------------------------------------- |
| action              | string  | Action name: user/getNetwork                                   |
| status              | string  | Operation execution status (success or error).                 |
| requestId           | object  | Request unique identifier as specified in the request message. |
| network             | object  | Associated network object.                                     |
| network.id          | integer | Network identifier.                                            |
| network.name        | string  | Network display name.                                          |
| network.description | string  | Network description.                                           |
