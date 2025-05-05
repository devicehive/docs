---
title: "configuration/delete"
slug: "configurationdelete"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 19 2017 11:35:09 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Deletes a property.

## Request Message

**Authorization**

Access JSON Web Token (ManageConfiguration)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "name": {string}
}
```

**Message Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: configuration/delete                                       |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| name          | Yes      | string | Configuration parameter name.                                           |

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
| action        | string | Action name: configuration/delete                              |
| status        | string | Operation execution status (success or error).                 |
| requestId     | object | Request unique identifier as specified in the request message. |
