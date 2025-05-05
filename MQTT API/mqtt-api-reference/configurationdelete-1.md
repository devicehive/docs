---
title: "configuration/delete"
slug: "configurationdelete-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:53:29 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:25:24 GMT+0000 (Coordinated Universal Time)"
---
Deletes a property.

**Authorization**

Access JSON Web Token (ManageConfiguration)

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
    "name": {string}
}
```

**Payload Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: configuration/delete                                       |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| name          | Yes      | string | Configuration parameter name.                                           |

## Response Topic and Payload

**Topic**

```text
dh/response/configuration/delete@{clientId}
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
| action        | string | Action name: configuration/delete                              |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
