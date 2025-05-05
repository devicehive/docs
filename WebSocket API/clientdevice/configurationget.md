---
title: "configuration/get"
slug: "configurationget"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 19 2017 11:34:46 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Returns requested property value.

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
| action        | Yes      | string | Action name: configuration/get                                          |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| name          | Yes      | string | Configuration parameter name.                                           |

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
| action                      | string  | Action name: configuration/get                                 |
| status                      | string  | Operation execution status (success or error).                 |
| requestId                   | object  | Request unique identifier as specified in the request message. |
| configuration               | object  | The [Configuration](doc:configuration) resource.               |
| configuration.name          | string  | Configuration parameter name.                                  |
| configuration.value         | string  | Configuration parameter value.                                 |
| configuration.entityVersion | integer | Specifies the version field or property of an entity class.    |
