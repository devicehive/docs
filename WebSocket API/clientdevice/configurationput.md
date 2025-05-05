---
title: "configuration/put"
slug: "configurationput"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 19 2017 11:34:57 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Creates new or updates existing property.

## Request Message

**Authorization**

Access JSON Web Token (ManageConfiguration)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "name": {string},
    "value": {string}
}
```

**Message Parameters**

| Property Name | Required | Type   | Description                                                             |
| :------------ | :------- | :----- | :---------------------------------------------------------------------- |
| action        | Yes      | string | Action name: configuration/put                                          |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| name          | Yes      | string | Configuration parameter name.                                           |
| value         | Yes      | string | Configuration parameter value.                                          |

## Server Message

**Message Representation**

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

**Message Parameters**

| Property Name               | Type    | Description                                                    |
| :-------------------------- | :------ | :------------------------------------------------------------- |
| action                      | string  | Action name: configuration/put                                 |
| status                      | string  | Operation execution status (success or error).                 |
| requestId                   | object  | Request unique identifier as specified in the request message. |
| configuration               | object  | The [Configuration](doc:configuration)  resource.              |
| configuration.name          | string  | Configuration parameter name.                                  |
| configuration.value         | string  | Configuration parameter value.                                 |
| configuration.entityVersion | integer | Specifies the version field or property of an entity class.    |
