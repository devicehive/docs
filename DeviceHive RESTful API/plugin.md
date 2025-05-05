---
title: "Plugin"
slug: "plugin"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Nov 15 2017 16:52:17 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jan 23 2018 10:27:22 GMT+0000 (Coordinated Universal Time)"
---
Represents a plugin to this API.

## Methods

| Method                     | Authorization                             | Uri                   | Description       |
| :------------------------- | :---------------------------------------- | :-------------------- | :---------------- |
| [register](doc:register-1) | Access JSON User Web Token (ManagePlugin) | POST /plugin/register | Registers plugin. |

## Resource Representation

```text
{
  "name": {string},
  "description": {string},
  "parameters": {object}
}
```

| Property Name | Type   | Description                 |
| :------------ | :----- | :-------------------------- |
| name          | string | Plugin name                 |
| description   | string | Plugin description          |
| parameters    | object | Json object with parameters |
