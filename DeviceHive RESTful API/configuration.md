---
title: "Configuration"
slug: "configuration"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jun 30 2017 12:29:20 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
Represents a configuration property.

## Methods

| Method               | Authorization                        | Uri                          | Description                               |
| :------------------- | :----------------------------------- | :--------------------------- | :---------------------------------------- |
| [get](doc:get-1)     | JSON Web Token (ManageConfiguration) | GET /configuration/{name}    | Returns requested property value.         |
| [put](doc:put)       | JSON Web Token (ManageConfiguration) | PUT /configuration/{name}    | Creates new or updates existing property. |
| [delete](doc:delete) | JSON Web Token (ManageConfiguration) | DELETE /configuration/{name} | Deletes a property.                       |

## Resource Representation

```text
{
    "name": {string},
    "value": {string},
    "entityVersion": {integer}
}
```

| Property Name | Type    | Description                                                 |
| :------------ | :------ | :---------------------------------------------------------- |
| name          | string  | Configuration parameter name                                |
| value         | string  | Configuration parameter value                               |
| entityVersion | integer | Specifies the version field or property of an entity class. |
