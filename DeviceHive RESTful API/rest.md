---
title: "REST API Reference"
slug: "rest"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jun 30 2017 12:28:15 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Thu Jan 11 2018 11:32:48 GMT+0000 (Coordinated Universal Time)"
---
The DeviceHive REST API exposes the following resources:

## Authentication

Provides a mechanism of authentication to this API.

For Authentication resource details, see the [resource representation](doc:authentication) page.

| Method                 | Authorization                       | Uri                 | Description                                                                         |
| :--------------------- | :---------------------------------- | :------------------ | :---------------------------------------------------------------------------------- |
| [login](doc:login)     | None                                | POST /token         | Creates and returns access and refresh tokens for the given user.                   |
| [create](doc:create)   | Access JSON Web Token (ManageToken) | POST /token/create  | Creates and returns access and refresh tokens for the given user and access rights. |
| [refresh](doc:refresh) | None                                | POST /token/refresh | Creates and returns a new access token for the given refresh token.                 |

## ApiInfo

Represents meta-information about the current API.

For ApiInfo resource details, see the [resource representation](doc:apiinfo) page.

| Method                       | Authorization | Uri                      | Description                                               |
| :--------------------------- | :------------ | :----------------------- | :-------------------------------------------------------- |
| [get](doc:get)               | None          | GET /info                | Gets meta-information of the current API.                 |
| [getCluster](doc:getcluster) | None          | GET /info/config/cluster | Returns information about cluster (Kafka, Zookeeper etc.) |

## Configuration

Represents a configuration property.

For Configuration resource details, see the [resource representation](doc:configuration) page.

| Method               | Authorization                        | Uri                          | Description                               |
| :------------------- | :----------------------------------- | :--------------------------- | :---------------------------------------- |
| [get](doc:get-1)     | JSON Web Token (ManageConfiguration) | GET /configuration/{name}    | Returns requested property value.         |
| [put](doc:put)       | JSON Web Token (ManageConfiguration) | PUT /configuration/{name}    | Creates new or updates existing property. |
| [delete](doc:delete) | JSON Web Token (ManageConfiguration) | DELETE /configuration/{name} | Deletes a property.                       |

## Device

Represents a device, a unit that runs microcode and communicates to this API.

For Device resource details, see the [resource representation](doc:device) page.

| Method                   | Authorization                          | Uri                 | Description                                                                                       |
| :----------------------- | :------------------------------------- | :------------------ | :------------------------------------------------------------------------------------------------ |
| [list](doc:list)         | Access JSON Web Token (GetDevice)      | GET /device         | Gets list of devices.                                                                             |
| [get](doc:get-2)         | Access JSON Web Token (GetDevice)      | GET /device/{id}    | Gets information about device.                                                                    |
| [register](doc:register) | Access JSON Web Token (RegisterDevice) | PUT /device/{id}    | Registers or updates a device. For initial device registration, only 'name' property is required. |
| [delete](doc:delete-1)   | Access JSON Web Token (RegisterDevice) | DELETE /device/{id} | Deletes an existing device.                                                                       |

## DeviceType

Represents a type of the device.

For DeviceType resource details, see the [resource representation](doc:devicetype) page.

[block:parameters]
{
  "data": {
    "h-0": "",
    "h-1": "",
    "h-2": "",
    "h-3": "",
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


## DeviceCommand

Represents a device command, a unit of information sent to devices.

For DeviceCommand resource details, see the [resource representation](doc:devicecommand) page.

[block:parameters]
{
  "data": {
    "h-0": "Method",
    "h-1": "Authorization",
    "h-2": "Uri",
    "h-3": "Description",
    "0-0": "[query](doc:query)",
    "0-1": "Access JSON Web Token (GetDeviceCommand)",
    "0-2": "GET /device/{deviceId}/command",
    "0-3": "Queries device commands.",
    "1-0": "[get](doc:get-3)",
    "1-1": "Access JSON Web Token (GetDeviceCommand)",
    "1-2": "GET /device/{deviceId}/command/{commandId}",
    "1-3": "Gets information about device command.",
    "2-0": "[insert](doc:insert)",
    "2-1": "Access JSON Web Token (CreateDeviceCommand)",
    "2-2": "POST /device/{deviceId}/command",
    "2-3": "Creates new device command.",
    "3-0": "[update](doc:update)",
    "3-1": "Access JSON Web Token (GetDeviceCommand)",
    "3-2": "GET /device/{deviceId}/command/poll",
    "3-3": "Updates an existing device command.",
    "4-0": "[poll](doc:poll)",
    "4-1": "Access JSON Web Token (GetDeviceCommand)",
    "4-2": "GET /device/{deviceId}/command/{commandId}/poll",
    "4-3": "Polls new device commands.  \nThis method returns all device commands that were created after specified timestamp.  \nIn the case when no commands were found, the method blocks until new command is received. If no commands are received within the waitTimeout period, the server returns an empty response. In this case, to continue polling, the client should repeat the call with the same timestamp value.",
    "5-0": "[wait](doc:wait)",
    "5-1": "Access JSON Web Token (GetDeviceCommand)",
    "5-2": "GET /device/{deviceId}/command/{commandId}/poll",
    "5-3": "Waits for a command to be processed.  \nThis method returns a command only if it has been processed by a device.  \nIn the case when command is not processed, the method blocks until device acknowledges command execution. If the command is not processed within the waitTimeout period, the server returns an empty response. In this case, to continue polling, the client should repeat the call.",
    "6-0": "[pollMany](doc:pollmany)",
    "6-1": "Access JSON Web Token (GetDeviceCommand)",
    "6-2": "GET /device/command/poll",
    "6-3": "Polls new device commands.  \nThis method returns all device commands that were created after specified timestamp.  \nIn the case when no commands were found, the method blocks until new command is received. If no commands are received within the waitTimeout period, the server returns an empty response. In this case, to continue polling, the client should repeat the call with the same timestamp value."
  },
  "cols": 4,
  "rows": 7,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


## DeviceNotification

Represents a device notification, a unit of information dispatched from devices.

For DeviceNotification resource details, see the [resource representation](doc:devicenotification) page.

[block:parameters]
{
  "data": {
    "h-0": "Method",
    "h-1": "Authorization",
    "h-2": "Uri",
    "h-3": "Description",
    "0-0": "[query](doc:query-1)",
    "0-1": "Access JSON Web Token (GetDeviceNotification)",
    "0-2": "GET /device/{deviceId}/notification",
    "0-3": "Queries device notifications.",
    "1-0": "[get](doc:get-4)",
    "1-1": "Access JSON Web Token (GetDeviceNotification)",
    "1-2": "GET /device/{deviceId}/notification/{id}",
    "1-3": "Gets information about device notification.",
    "2-0": "[insert](doc:insert-1)",
    "2-1": "Access JSON Web Token (CreateDeviceNotification)",
    "2-2": "POST /device/{deviceId}/notification",
    "2-3": "Creates new device notification.",
    "3-0": "[poll](doc:poll-1)",
    "3-1": "Access JSON Web Token (GetDeviceNotification)",
    "3-2": "GET /device/{deviceId}/notification/poll",
    "3-3": "Polls new device notifications.  \nThis method returns all device notifications that were created after specified timestamp.  \nIn the case when no notifications were found, the method blocks until new notification is received. If no notifications are received within the waitTimeout period, the server returns an empty response. In this case, to continue polling, the client should repeat the call with the same timestamp value.",
    "4-0": "[pollMany](doc:pollmany-1)",
    "4-1": "Access JSON Web Token (GetDeviceNotification)",
    "4-2": "GET /device/notification/poll",
    "4-3": "Polls new device notifications.  \nThis method returns all device notifications that were created after specified timestamp.  \nIn the case when no notifications were found, the method blocks until new notification is received. If no notifications are received within the waitTimeout period, the server returns an empty response. In this case, to continue polling, the client should repeat the call with the same timestamp value."
  },
  "cols": 4,
  "rows": 5,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


## Network

Represents a network, an isolated area where devices reside.

For Network resource details, see the [resource representation](doc:network) page.

[block:parameters]
{
  "data": {
    "h-0": "Method",
    "h-1": "Authorization",
    "h-2": "Uri",
    "h-3": "Description",
    "0-0": "[list](doc:list-1)",
    "0-1": "Access JSON Web Token (GetNetwork)",
    "0-2": "GET /network",
    "0-3": "Gets list of device networks.  \nThe result list is limited to networks the client has access to.",
    "1-0": "[get](doc:get-5)",
    "1-1": "Access JSON Web Token (GetNetwork)",
    "1-2": "GET /network/{id}",
    "1-3": "Gets information about device network and its devices.",
    "2-0": "[insert](doc:insert-2)",
    "2-1": "Access JSON Web Token (ManageNetwork)",
    "2-2": "POST /network",
    "2-3": "Creates new device network.",
    "3-0": "[update](doc:update-1)",
    "3-1": "Access JSON Web Token (ManageNetwork)",
    "3-2": "PUT /network/{id}",
    "3-3": "Updates an existing device network.",
    "4-0": "[delete](doc:delete-2)",
    "4-1": "Access JSON Web Token (ManageNetwork)",
    "4-2": "DELETE /network/{id}",
    "4-3": "Deletes an existing device network."
  },
  "cols": 4,
  "rows": 5,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


## User

Represents a user to this API.

For User resource details, see the [resource representation](doc:user) page.

[block:parameters]
{
  "data": {
    "h-0": "Method",
    "h-1": "Authorization",
    "h-2": "Uri",
    "h-3": "Description",
    "0-0": "[list](doc:list-2)",
    "0-1": "Access JSON Web Token (ManageUser)",
    "0-2": "GET /user",
    "0-3": "Gets list of users.",
    "1-0": "[get](doc:get-6)",
    "1-1": "Access JSON Web Token (GetCurrentUser)",
    "1-2": "GET /user/{id}",
    "1-3": "Gets information about user and its assigned networks.  \nOnly administrators are allowed to get information about any user. User-level accounts can only retrieve information about themselves.",
    "2-0": "[insert](doc:insert-3)",
    "2-1": "Access JSON Web Token (ManageUser)",
    "2-2": "POST /user",
    "2-3": "Creates new user.",
    "3-0": "[update](doc:update-2)",
    "3-1": "Access JSON Web Token (UpdateCurrentUser)",
    "3-2": "PUT /user/{id}",
    "3-3": "Updates an existing user.  \nOnly administrators are allowed to update any property of any user. User-level accounts can only change their own password in case:  \n  _ They already have a password.  \n  _ They provide a valid current password in the 'oldPassword' property. ",
    "4-0": "[delete](doc:delete-3)",
    "4-1": "Access JSON Web Token (ManageUser)",
    "4-2": "DELETE /user/{id}",
    "4-3": "Deletes an existing user.",
    "5-0": "[getCurrent](doc:getcurrent)",
    "5-1": "Access JSON Web Token (ManageUser)",
    "5-2": "GET /user/current",
    "5-3": "Gets information about user/network association.  \nOnly administrators are allowed to get information about any user. User-level accounts can only retrieve information about themselves.",
    "6-0": "[updateCurrent](doc:updatecurrent)",
    "6-1": "Access JSON Web Token (ManageUser)",
    "6-2": "PUT /user/current",
    "6-3": "Updates the current user.  \nOnly administrators are allowed to update any property of any user. User-level accounts can only change their own password in case:  \n  _ They already have a password.  \n  _ They provide a valid current password in the 'oldPassword' property. ",
    "7-0": "[getNetwork](doc:getnetwork)",
    "7-1": "Access JSON Web Token (ManageUser)",
    "7-2": "GET /user/{id}/network/{networkId}",
    "7-3": "Gets information about user/network association.",
    "8-0": "[assignNetwork](doc:assignnetwork)",
    "8-1": "Access JSON Web Token (ManageUser)",
    "8-2": "PUT /user/{id}/network/{networkId}",
    "8-3": "Associates network with the user.",
    "9-0": "[unassignNetwork](doc:unassignnetwork)",
    "9-1": "Access JSON Web Token (ManageUser)",
    "9-2": "DELETE /user/{id}/network/{networkId}",
    "9-3": "Removes association between network and user."
  },
  "cols": 4,
  "rows": 10,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]
