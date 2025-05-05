---
title: "server/info"
slug: "serverinfo-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 13:01:47 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:32:57 GMT+0000 (Coordinated Universal Time)"
---
Gets meta-information about the current API.

**Authorization**

None

## Request Topic and Payload

**Topic**

```text
dh/request
```

**Payload Representation**

```text
{
    "action": {string},
    "requestId": {object}
}
```

**Payload Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: server/info                                                |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |

## Response Topic and Payload

**Topic**

```text
dh/response/authenticate@{clientId}
```

**Payload Representation**

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

**Payload Parameters**

| Property Name        | Type     | Description                                                    |
| :------------------- | :------- | :------------------------------------------------------------- |
| action               | string   | Action name: server/info                                       |
| status               | string   | Operation execution status (success or error).                 |
| requestId            | object   | Request unique identifier as specified in the request message. |
| info                 | object   | The [ApiInfo](doc:apiinfo)  resource.                          |
| info.apiVersion      | string   | API version.                                                   |
| info.serverTimestamp | datetime | Current server timestamp.                                      |
| info.restServerUrl   | string   | REST server URL.                                               |
