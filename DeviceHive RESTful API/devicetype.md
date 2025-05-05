---
title: "DeviceType"
slug: "devicetype"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jan 10 2018 12:46:11 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Jan 10 2018 14:38:28 GMT+0000 (Coordinated Universal Time)"
---
Represents a type of the device.

## Methods

[block:parameters]
{
  "data": {
    "h-0": "Method",
    "h-1": "Authorization",
    "h-2": "Uri",
    "h-3": "Description",
    "0-0": "[list](doc:list-3)",
    "0-1": "Access JSON Web Token (GetDeviceType)",
    "0-2": "GET /devicetype",
    "0-3": "Gets list of device types.  \nThe result list is limited to device types the client has access to.",
    "1-0": "[count](doc:count-3)",
    "1-1": "Access JSON Web Token (GetDeviceType)",
    "1-2": "GET /devicetype/count",
    "1-3": "Gets count of device types the client has access to.",
    "2-0": "[get](doc:get-7)",
    "2-1": "Access JSON Web Token (GetDeviceType)",
    "2-2": "GET /devicetype/{id}",
    "2-3": "Gets information about device type and its devices.",
    "3-0": "[insert](doc:insert-4)",
    "3-1": "Access JSON Web Token (ManageDeviceType)",
    "3-2": "POST /devicetype",
    "3-3": "Creates new device type.",
    "4-0": "[update](doc:update-3)",
    "4-1": "Access JSON Web Token (ManageDeviceType)",
    "4-2": "PUT /devicetype/{id}",
    "4-3": "Updates an existing device type.",
    "5-0": "[delete](doc:delete-4)",
    "5-1": "Access JSON Web Token (ManageDeviceType)",
    "5-2": "DELETE /devicetype/{id}",
    "5-3": "Deletes an existing device type."
  },
  "cols": 4,
  "rows": 6,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


## Resource Representation

```text
{
    "id": {integer},
    "name": {string},
    "description": {string}
}
```

| Property Name | Type    | Description              |
| :------------ | :------ | :----------------------- |
| id            | integer | Device type identifier.  |
| name          | string  | Device type name.        |
| description   | string  | Device type description. |
