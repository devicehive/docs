---
title: "configuration/get"
slug: "configurationget-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Thu Feb 08 2018 12:53:08 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Feb 08 2018 13:09:34 GMT+0000 (Coordinated Universal Time)"
---
Returns requested property value.

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
| action        | Yes      | string | Action name: configuration/get                                          |
| requestId     | No       | object | Request unique identifier, will be passed back in the response message. |
| name          | Yes      | string | Configuration parameter name.                                           |

## Response Topic and Payload

**Topic**

```text
dh/response/configuration/get@{clientId}
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

**Payload Parameters**

| Property Name               | Type    | Description                                                    |
| :-------------------------- | :------ | :------------------------------------------------------------- |
| action                      | string  | Action name: configuration/get                                 |
| status                      | string  | Operation execution status (success or error).                 |
| requestId                   | object  | Request unique identifier as specified in the request message. |
| configuration               | object  | The [Configuration](doc:configuration) resource.               |
| configuration.name          | string  | Configuration parameter name.                                  |
| configuration.value         | string  | Configuration parameter value.                                 |
| configuration.entityVersion | integer | Specifies the version field or property of an entity class.    |
