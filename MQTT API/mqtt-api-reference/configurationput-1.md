---
title: "configuration/put"
slug: "configurationput-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:53:19 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 15:23:36 GMT+0000 (Coordinated Universal Time)"
---
Creates new or updates existing property.

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
    "name": {string},
    "value": {string}
}
```

**Payload Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: configuration/put                                          |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| name          | Yes      | string | Configuration parameter name.                                           |
| value         | Yes      | string | Configuration parameter value.                                          |

## Response Topic and Payload

**Topic**

```text
dh/response/configuration/put@{clientId}
```

**Payload Representation**

```text
{
    "action": {string},
    "status": {string},
    "requestId": {object},
    "configuration": {
        "name": {string},
        "value": {string},
        "entityVersion": {integer}
    }
}
```

| Property Name               | Type    | Description                                                    |
| :-------------------------- | :------ | :------------------------------------------------------------- |
| action                      | string  | Action name: configuration/put                                 |
| status                      | string  | Operation execution status (success or error).                 |
| requestId                   | object  | Request unique identifier as specified in the request message. |
| configuration               | object  | The [Configuration](doc:configuration)  resource.              |
| configuration.name          | string  | Configuration parameter name.                                  |
| configuration.value         | string  | Configuration parameter value.                                 |
| configuration.entityVersion | integer | Specifies the version field or property of an entity class.    |
