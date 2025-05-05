---
title: "DeviceCommand"
slug: "devicecommand"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jun 30 2017 12:30:06 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Mon Jan 22 2018 16:07:44 GMT+0000 (Coordinated Universal Time)"
---
Represents a device command, a unit of information sent to devices.

## Methods

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
    "3-1": "Access JSON Web Token (UpdateDeviceCommand)",
    "3-2": "PUT /device/{deviceId}/command/{commandId}",
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


## Resource Representation

```text
{
    "id": {integer},
    "timestamp": {datetime},
    "userId": {integer},
    "deviceId": {string},
    "networkId": {integer},
    "deviceTypeId": {integer},
    "command": {string},
    "parameters": {object},
    "lifetime": {integer},
    "status": {string},
    "result": {object},
    "lastUpdated": {datetime}
}
```

| Property Name | Type     | Description                                                                                                      |
| :------------ | :------- | :--------------------------------------------------------------------------------------------------------------- |
| id            | integer  | Command identifier.                                                                                              |
| command       | string   | Command name                                                                                                     |
| timestamp     | datetime | Command UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)).             |
| userId        | integer  | Associated user identifier.                                                                                      |
| deviceId      | string   | Device unique identifier.                                                                                        |
| networkId     | integer  | Network unique identifier.                                                                                       |
| deviceTypeId  | integer  | Device type unique identifier.                                                                                   |
| parameters    | object   | Command parameters, a JSON object with an arbitrary structure.                                                   |
| lifetime      | integer  | Command lifetime, a number of seconds until this command expires.                                                |
| status        | string   | Command status, as reported by device or related infrastructure.                                                 |
| result        | object   | Command execution result, an optional value that could be provided by device.                                    |
| lastUpdated   | datetime | Last command update UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)). |
