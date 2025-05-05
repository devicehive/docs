---
title: "user/getNetwork"
slug: "usergetnetwork"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Jul 31 2017 07:30:33 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Gets information about user/network association.

## Request Message

**Authorization**

Access JSON Web Token (ManageUser)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "userId": {integer},
    "networkId": {integer}
}
```

**Message Parameters**

| Parameter Name | Required | Type    | Description                                                             |
| :------------- | :------- | :------ | :---------------------------------------------------------------------- |
| action         | Yes      | string  | Action name: user/getNetwork                                            |
| requestId      | No       | object  | Request unique identifier, will be passed back in the response message. |
| userId         | Yes      | integer | User identifier                                                         |
| networkId      | Yes      | integer | Network identifier                                                      |

## Server Message

If successful, this method returns the following structure in the response body.

**Message Representation**

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

**Message Parameters**

| Property Name       | Type    | Description                                                    |
| :------------------ | :------ | :------------------------------------------------------------- |
| action              | string  | Action name: user/getNetwork                                   |
| status              | string  | Operation execution status (success or error).                 |
| requestId           | object  | Request unique identifier as specified in the request message. |
| network             | object  | Associated network object.                                     |
| network.id          | integer | Network identifier.                                            |
| network.name        | string  | Network display name.                                          |
| network.description | string  | Network description.                                           |
