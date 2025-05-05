---
title: "command/list"
slug: "commandlist"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Jul 12 2017 19:19:24 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Nov 07 2017 23:22:06 GMT+0000 (Coordinated Universal Time)"
---
Gets the list of commands.

## Request Message

**Authorization**

Access JSON Web Token (GetDeviceCommand)

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "deviceId": {string},
    "start": {datetime},
    "end": {datetime},
    "command": {string},
    "status": {string},
    "sortField": {string},
    "sortOrder": {string},
    "take": {integer},
    "skip": {integer}
}
```

**Message Parameters**

| Property Name | Required | Type     | Description                                                                                                           |
| :------------ | :------- | :------- | :-------------------------------------------------------------------------------------------------------------------- |
| action        | Yes      | string   | Action name: command/list                                                                                             |
| requestId     | No       | object   | Request unique identifier, will be passed back in the response message.                                               |
| deviceId      | Yes      | string   | Device unique identifier.                                                                                             |
| start         | No       | datetime | Start UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)) to filter commands. |
| end           | No       | datetime | End UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)) to filter commands.   |
| command       | No       | string   | Filter by command name.                                                                                               |
| status        | No       | string   | Filter by command status.                                                                                             |
| sortField     | No       | string   | Result list sort field.                                                                                               |
| sortOrder     | No       | string   | Result list sort order. Available values are ASC and DESC. The sortField should be specified.                         |
| take          | No       | integer  | Number of records to take from the result list. If not specified 100 records will be taken.                           |
| skip          | No       | integer  | Number of records to skip from the result list. If not specified 0 records will be skipped.                           |

## Server Message

**Message Representation**

```text
{
    "action": {string},
    "requestId": {object},
    "status": {string},
    "commands": [{
        "id": {long},
        "command": {string},
        "timestamp": {datetime},
        "lastUpdated": {datetime},
        "userId": {integer},
        "deviceId": {string},
        "networkId": {integer},
        "parameters": {object},
        "lifetime": {integer},
        "status": {string},
        "result": {object}
    }]
            
}
```

**Message Parameters**

| Property Name       | Type     | Description                                                                                                      |
| :------------------ | :------- | :--------------------------------------------------------------------------------------------------------------- |
| action              | string   | Action name: command/list                                                                                        |
| requestId           | object   | Request unique identifier as specified in the request message.                                                   |
| status              | string   | Operation execution status (success or error).                                                                   |
| commands            | array    | The array of commands.                                                                                           |
| command             | object   | An inserted [DeviceCommand](doc:devicecommand)   resource.                                                       |
| command.id          | long     | Command identifier.                                                                                              |
| command.command     | string   | Command name.                                                                                                    |
| command.timestamp   | datetime | Command UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)).             |
| command.lastUpdated | datetime | Last command update UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)). |
| command.userId      | integer  | Associated user identifier.                                                                                      |
| command.deviceId    | string   | Associated device identifier.                                                                                    |
| command.networkId   | integer  | Associated network identifier.                                                                                   |
| command.parameters  | object   | Command parameters, a JSON object with an arbitrary structure.                                                   |
| command.lifetime    | integer  | Command lifetime, a number of seconds until this command expires.                                                |
| command.status      | string   | Command status, as reported by device or related infrastructure.                                                 |
| command.result      | object   | Command execution result, an optional value that could be provided by device.                                    |
