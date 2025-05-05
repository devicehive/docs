---
title: "server/info"
slug: "serverinfo"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Sat Jul 15 2017 12:46:37 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Gets meta-information about the current API.

## Request Message

**Authorization**

None

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object}
}
```

**Message Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: server/info                                                |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |

## Response Message

**Message Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "info": {
        "apiVersion": {string},
        "serverTimestamp": {datetime},
        "restServerUrl": {string}
    }
}
```

**Message Parameters**

| Property Name        | Type     | Description                                                    |
| :------------------- | :------- | :------------------------------------------------------------- |
| action               | string   | Action name: server/info                                       |
| status               | string   | Operation execution status (success or error).                 |
| requestId            | object   | Request unique identifier as specified in the request message. |
| info                 | object   | The [ApiInfo](doc:apiinfo)  resource.                          |
| info.apiVersion      | string   | API version.                                                   |
| info.serverTimestamp | datetime | Current server timestamp.                                      |
| info.restServerUrl   | string   | REST server URL.                                               |
