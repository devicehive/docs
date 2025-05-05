---
title: "Device"
slug: "device"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jun 30 2017 12:29:28 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Jan 10 2018 14:47:16 GMT+0000 (Coordinated Universal Time)"
---
Represents a device, a unit that runs microcode and communicates to this API.

## Methods

| Method                   | Authorization                          | Uri                 | Description                                                                                       |
| :----------------------- | :------------------------------------- | :------------------ | :------------------------------------------------------------------------------------------------ |
| [list](doc:list)         | Access JSON Web Token (GetDevice)      | GET /device         | Gets list of devices.                                                                             |
| [count](doc:count)       | Access JSON Web Token (GetDevice)      | GET /device/count   | Gets count of devices.                                                                            |
| [get](doc:get-2)         | Access JSON Web Token (GetDevice)      | GET /device/{id}    | Gets information about device.                                                                    |
| [register](doc:register) | Access JSON Web Token (RegisterDevice) | PUT /device/{id}    | Registers or updates a device. For initial device registration, only 'name' property is required. |
| [delete](doc:delete-1)   | Access JSON Web Token (RegisterDevice) | DELETE /device/{id} | Deletes an existing device.                                                                       |

## Resource Representation

```text
{
    "id": {string},
    "name": {string},
    "data": {object},
    "networkId": {integer},
    "deviceTypeId": {integer},
    "isBlocked": {boolean}
}
```

| Property Name | Type    | Description                                             |
| :------------ | :------ | :------------------------------------------------------ |
| id            | string  | Device unique identifier.                               |
| name          | string  | Device display name.                                    |
| data          | object  | Device data, a JSON object with an arbitrary structure. |
| networkId     | integer | Associated network id.                                  |
| deviceTypeId  | integer | Associated device type id.                              |
| isBlocked     | boolean | Indicates whether device is blocked.                    |
