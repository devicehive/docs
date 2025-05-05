---
title: "RESTfult HTTP Operations"
slug: "restful-over-http"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jul 24 2015 05:50:32 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
### Logout

```
DELETE /auth/accesskey
```

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Consumes

- application/json

#### Tags

- Authentication

### Login

```
POST /auth/accesskey
```

#### Parameters

| Type          | Name | Description        | Required | Schema           | Default |
| ------------- | ---- | ------------------ | -------- | ---------------- | ------- |
| BodyParameter | body | Access key request | true     | AccessKeyRequest |         |

#### Responses

| HTTP Code | Description                         | Schema     |
| --------- | ----------------------------------- | ---------- |
| 403       | If identity provider is not allowed | No Content |

#### Consumes

- application/json

#### Tags

- Authentication

### Get property

```
GET /configuration/{name}
```

#### Description

Returns requested property value

#### Parameters

| Type          | Name | Description   | Required | Schema | Default |
| ------------- | ---- | ------------- | -------- | ------ | ------- |
| PathParameter | name | Property name | true     | string |         |

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Consumes

- application/json

#### Tags

- Configuration

### Create or update property

```
PUT /configuration/{name}
```

#### Description

Creates new or updates existing property

#### Parameters

| Type          | Name | Description    | Required | Schema | Default |
| ------------- | ---- | -------------- | -------- | ------ | ------- |
| PathParameter | name | Property name  | true     | string |         |
| BodyParameter | body | Property value | true     | string |         |

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Consumes

- application/json

#### Tags

- Configuration

### Delete property

```
DELETE /configuration/{name}
```

#### Description

Deletes property

#### Parameters

| Type          | Name | Description   | Required | Schema | Default |
| ------------- | ---- | ------------- | -------- | ------ | ------- |
| PathParameter | name | Property name | true     | string |         |

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Consumes

- application/json

#### Tags

- Configuration

### Create or update property

```
GET /configuration/{name}/set
```

#### Description

Creates new or updates existing property

#### Parameters

| Type           | Name  | Description    | Required | Schema | Default |
| -------------- | ----- | -------------- | -------- | ------ | ------- |
| PathParameter  | name  | Property name  | true     | string |         |
| QueryParameter | value | Property value | true     | string |         |

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Consumes

- application/json

#### Tags

- Configuration

### List devices

```
GET /device
```

#### Description

Gets list of devices.

#### Parameters

| Type           | Name               | Description                                     | Required | Schema                                    | Default |
| -------------- | ------------------ | ----------------------------------------------- | -------- | ----------------------------------------- | ------- |
| QueryParameter | name               | Filter by device name.                          | false    | string                                    |         |
| QueryParameter | namePattern        | Filter by device name pattern.                  | false    | string                                    |         |
| QueryParameter | status             | Filter by device status.                        | false    | string                                    |         |
| QueryParameter | networkId          | Filter by associated network identifier.        | false    | integer (int64)                           |         |
| QueryParameter | networkName        | Filter by associated network name.              | false    | string                                    |         |
| QueryParameter | deviceClassId      | Filter by associated device class identifier.   | false    | integer (int64)                           |         |
| QueryParameter | deviceClassName    | Filter by associated device class name.         | false    | string                                    |         |
| QueryParameter | deviceClassVersion | Filter by associated device class version.      | false    | string                                    |         |
| QueryParameter | sortField          | Result list sort field.                         | false    | enum (Name, Status, Network, DeviceClass) |         |
| QueryParameter | sortOrder          | Result list sort order.                         | false    | enum (ASC, DESC)                          |         |
| QueryParameter | take               | Number of records to take from the result list. | false    | integer (int32)                           | 20      |
| QueryParameter | skip               | Number of records to skip from the result list. | false    | integer (int32)                           | 0       |

#### Responses

| HTTP Code | Description                                                                        | Schema       |
| --------- | ---------------------------------------------------------------------------------- | ------------ |
| 200       | If successful, this method returns array of Device resources in the response body. | Device array |
| 400       | If request parameters invalid                                                      | No Content   |
| 401       | If request is not authorized                                                       | No Content   |
| 403       | If principal doesn't have permissions                                              | No Content   |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- Device

### List device classes

```
GET /device/class
```

#### Description

Gets list of device classes.

#### Parameters

| Type           | Name        | Description                                     | Required | Schema           | Default |
| -------------- | ----------- | ----------------------------------------------- | -------- | ---------------- | ------- |
| QueryParameter | name        | Filter by device class name.                    | false    | string           |         |
| QueryParameter | namePattern | Filter by device class name pattern.            | false    | string           |         |
| QueryParameter | version     | Filter by device class version.                 | false    | string           |         |
| QueryParameter | sortField   | Result list sort field.                         | false    | enum (ID, Name)  |         |
| QueryParameter | sortOrder   | Result list sort order.                         | false    | enum (ASC, DESC) |         |
| QueryParameter | take        | Number of records to take from the result list. | false    | integer (int32)  | 20      |
| QueryParameter | skip        | Number of records to skip from the result list. | false    | integer (int32)  | 0       |

#### Responses

| HTTP Code | Description                                                                             | Schema            |
| --------- | --------------------------------------------------------------------------------------- | ----------------- |
| 200       | If successful, this method returns array of DeviceClass resources in the response body. | DeviceClass array |
| 400       | If request parameters invalid                                                           | No Content        |
| 401       | If request is not authorized                                                            | No Content        |
| 403       | If principal doesn't have permissions                                                   | No Content        |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- DeviceClass

### Create device class

```
POST /device/class
```

#### Description

Creates new device class.

#### Parameters

| Type          | Name | Description       | Required | Schema      | Default |
| ------------- | ---- | ----------------- | -------- | ----------- | ------- |
| BodyParameter | body | Device class body | true     | DeviceClass |         |

#### Responses

| HTTP Code | Description                                                                     | Schema      |
| --------- | ------------------------------------------------------------------------------- | ----------- |
| 201       | If successful, this method returns a DeviceClass resource in the response body. | DeviceClass |
| 400       | If request is malformed                                                         | No Content  |
| 401       | If request is not authorized                                                    | No Content  |
| 403       | If principal doesn't have permissions or device class with same name exists.    | No Content  |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- DeviceClass

### Create equipment

```
POST /device/class/{deviceClassId}/equipment
```

#### Description

Creates equipment

#### Parameters

| Type          | Name          | Description     | Required | Schema          | Default |
| ------------- | ------------- | --------------- | -------- | --------------- | ------- |
| PathParameter | deviceClassId | Device class id | true     | integer (int64) |         |
| BodyParameter | body          | Equipment body  | true     | Equipment       |         |

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Consumes

- application/json

#### Tags

- DeviceClass

### Get equipment

```
GET /device/class/{deviceClassId}/equipment/{id}
```

#### Description

Returns equipment by device class id and equipment id

#### Parameters

| Type          | Name          | Description     | Required | Schema          | Default |
| ------------- | ------------- | --------------- | -------- | --------------- | ------- |
| PathParameter | deviceClassId | Device class id | true     | integer (int64) |         |
| PathParameter | id            | Equipment id    | true     | integer (int64) |         |

#### Responses

| HTTP Code | Description            | Schema     |
| --------- | ---------------------- | ---------- |
| 404       | If equipment not found | No Content |

#### Tags

- DeviceClass

### Update equipment

```
PUT /device/class/{deviceClassId}/equipment/{id}
```

#### Description

Updates equipment

#### Parameters

| Type          | Name          | Description     | Required | Schema          | Default |
| ------------- | ------------- | --------------- | -------- | --------------- | ------- |
| PathParameter | deviceClassId | Device class id | true     | integer (int64) |         |
| PathParameter | id            | Equipment id    | true     | integer (int64) |         |
| BodyParameter | body          | Equipment body  | true     | EquipmentUpdate |         |

#### Responses

| HTTP Code | Description            | Schema     |
| --------- | ---------------------- | ---------- |
| 404       | If equipment not found | No Content |

#### Consumes

- application/json

#### Tags

- DeviceClass

### Delete equipment

```
DELETE /device/class/{deviceClassId}/equipment/{id}
```

#### Description

Deletes equipment

#### Parameters

| Type          | Name          | Description     | Required | Schema          | Default |
| ------------- | ------------- | --------------- | -------- | --------------- | ------- |
| PathParameter | deviceClassId | Device class id | true     | integer (int64) |         |
| PathParameter | id            | Equipment id    | true     | integer (int64) |         |

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Consumes

- application/json

#### Tags

- DeviceClass

### Get device class

```
GET /device/class/{id}
```

#### Description

Gets information about device class and its equipment.

#### Parameters

| Type          | Name | Description              | Required | Schema          | Default |
| ------------- | ---- | ------------------------ | -------- | --------------- | ------- |
| PathParameter | id   | Device class identifier. | true     | integer (int64) |         |

#### Responses

| HTTP Code | Description                                                                     | Schema      |
| --------- | ------------------------------------------------------------------------------- | ----------- |
| 200       | If successful, this method returns a DeviceClass resource in the response body. | DeviceClass |
| 400       | If request is malformed                                                         | No Content  |
| 401       | If request is not authorized                                                    | No Content  |
| 403       | If principal doesn't have permissions                                           | No Content  |
| 404       | If device class not found                                                       | No Content  |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- DeviceClass

### Update device class

```
PUT /device/class/{id}
```

#### Description

Updates an existing device class.

#### Parameters

| Type          | Name | Description              | Required | Schema            | Default |
| ------------- | ---- | ------------------------ | -------- | ----------------- | ------- |
| PathParameter | id   | Device class identifier. | true     | integer (int64)   |         |
| BodyParameter | body | Device class body        | true     | DeviceClassUpdate |         |

#### Responses

| HTTP Code | Description                                                | Schema     |
| --------- | ---------------------------------------------------------- | ---------- |
| 400       | If request is malformed                                    | No Content |
| 401       | If request is not authorized                               | No Content |
| 204       | If successful, this method returns an empty response body. | No Content |
| 403       | If principal doesn't have permissions                      | No Content |
| 404       | If device class is not found                               | No Content |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- DeviceClass

### Update device class

```
DELETE /device/class/{id}
```

#### Description

Deletes an existing device class.

#### Parameters

| Type          | Name | Description              | Required | Schema          | Default |
| ------------- | ---- | ------------------------ | -------- | --------------- | ------- |
| PathParameter | id   | Device class identifier. | true     | integer (int64) |         |

#### Responses

| HTTP Code | Description                                                | Schema     |
| --------- | ---------------------------------------------------------- | ---------- |
| 401       | If request is not authorized                               | No Content |
| 204       | If successful, this method returns an empty response body. | No Content |
| 403       | If principal doesn't have permissions                      | No Content |
| 404       | If access key is not found                                 | No Content |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- DeviceClass

### Poll for commands

```
GET /device/command/poll
```

#### Description

Polls for commands based on provided parameters (long polling)

#### Parameters

| Type           | Name        | Description             | Required | Schema          | Default |
| -------------- | ----------- | ----------------------- | -------- | --------------- | ------- |
| QueryParameter | deviceGuids | Device guids            | false    | string          |         |
| QueryParameter | names       | Command names           | false    | string          |         |
| QueryParameter | timestamp   | Timestamp to start from | false    | string          |         |
| QueryParameter | waitTimeout | Wait timeout            | false    | integer (int64) | 30      |
| BodyParameter  | body        |                         | false    | AsyncResponse   |         |

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Consumes

- application/json

#### Tags

- DeviceCommand

### Poll for notifications

```
GET /device/notification/poll
```

#### Description

Polls for notifications based on provided parameters (long polling)

#### Parameters

| Type           | Name        | Description             | Required | Schema          | Default |
| -------------- | ----------- | ----------------------- | -------- | --------------- | ------- |
| QueryParameter | waitTimeout | Wait timeout            | false    | integer (int64) | 30      |
| QueryParameter | deviceGuids | Device guids            | false    | string          |         |
| QueryParameter | names       | Notification names      | false    | string          |         |
| QueryParameter | timestamp   | Timestamp to start from | false    | string          |         |
| BodyParameter  | body        |                         | false    | AsyncResponse   |         |

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Tags

- DeviceNotification

### Query commands

```
GET /device/{deviceGuid}/command
```

#### Description

Gets list of commands

#### Parameters

| Type           | Name         | Description     | Required | Schema          | Default |
| -------------- | ------------ | --------------- | -------- | --------------- | ------- |
| PathParameter  | deviceGuid   | Device GUID     | true     | string          |         |
| QueryParameter | start        | Start timestamp | false    | string          |         |
| QueryParameter | end          | End timestamp   | false    | string          |         |
| QueryParameter | command      | Command name    | false    | string          |         |
| QueryParameter | status       | Command status  | false    | string          |         |
| QueryParameter | sortField    | Sort field      | false    | string          |         |
| QueryParameter | sortOrder    | Sort order      | false    | string          |         |
| QueryParameter | take         | Limit param     | false    | integer (int32) |         |
| QueryParameter | skip         | Skip param      | false    | integer (int32) |         |
| QueryParameter | gridInterval | Grid interval   | false    | integer (int32) |         |

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Consumes

- application/json

#### Tags

- DeviceCommand

### Insert command

```
POST /device/{deviceGuid}/command
```

#### Description

Inserts command

#### Parameters

| Type          | Name       | Description  | Required | Schema               | Default |
| ------------- | ---------- | ------------ | -------- | -------------------- | ------- |
| PathParameter | deviceGuid | Device GUID  | true     | string               |         |
| BodyParameter | body       | Command body | true     | DeviceCommandWrapper |         |

#### Responses

| HTTP Code | Description         | Schema     |
| --------- | ------------------- | ---------- |
| 404       | If device not found | No Content |

#### Consumes

- application/json

#### Tags

- DeviceCommand

### Poll for commands

```
GET /device/{deviceGuid}/command/poll
```

#### Description

Polls for commands based on provided parameters (long polling)

#### Parameters

| Type           | Name        | Description             | Required | Schema          | Default |
| -------------- | ----------- | ----------------------- | -------- | --------------- | ------- |
| PathParameter  | deviceGuid  | Device GUID             | true     | string          |         |
| QueryParameter | names       | Command names           | false    | string          |         |
| QueryParameter | timestamp   | Timestamp to start from | false    | string          |         |
| QueryParameter | waitTimeout | Wait timeout            | false    | integer (int64) | 30      |
| BodyParameter  | body        |                         | false    | AsyncResponse   |         |

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Consumes

- application/json

#### Tags

- DeviceCommand

### Get command

```
GET /device/{deviceGuid}/command/{commandId}
```

#### Description

Gets command by device id and command id

#### Parameters

| Type          | Name       | Description | Required | Schema | Default |
| ------------- | ---------- | ----------- | -------- | ------ | ------- |
| PathParameter | deviceGuid | Device GUID | true     | string |         |
| PathParameter | commandId  | Command Id  | true     | string |         |

#### Responses

| HTTP Code | Description                    | Schema     |
| --------- | ------------------------------ | ---------- |
| 404       | If device or command not found | No Content |

#### Consumes

- application/json

#### Tags

- DeviceCommand

### Update command

```
PUT /device/{deviceGuid}/command/{commandId}
```

#### Description

Update command

#### Parameters

| Type          | Name       | Description  | Required | Schema               | Default |
| ------------- | ---------- | ------------ | -------- | -------------------- | ------- |
| PathParameter | deviceGuid | Device GUID  | true     | string               |         |
| PathParameter | commandId  | Command Id   | true     | integer (int64)      |         |
| BodyParameter | body       | Command body | true     | DeviceCommandWrapper |         |

#### Responses

| HTTP Code | Description                    | Schema     |
| --------- | ------------------------------ | ---------- |
| 404       | If device or command not found | No Content |

#### Consumes

- application/json

#### Tags

- DeviceCommand

### Poll for commands

```
GET /device/{deviceGuid}/command/{commandId}/poll
```

#### Description

Polls for commands based on provided parameters (long polling)

#### Parameters

| Type           | Name        | Description  | Required | Schema          | Default |
| -------------- | ----------- | ------------ | -------- | --------------- | ------- |
| PathParameter  | deviceGuid  | Device GUID  | true     | string          |         |
| PathParameter  | commandId   | Command Id   | true     | string          |         |
| QueryParameter | waitTimeout | Wait timeout | false    | integer (int64) | 30      |
| BodyParameter  | body        |              | false    | AsyncResponse   |         |

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Consumes

- application/json

#### Tags

- DeviceCommand

### Get notifications

```
GET /device/{deviceGuid}/notification
```

#### Description

Returns notifications by provided parameters

#### Parameters

| Type           | Name         | Description       | Required | Schema          | Default |
| -------------- | ------------ | ----------------- | -------- | --------------- | ------- |
| PathParameter  | deviceGuid   | Device GUID       | true     | string          |         |
| QueryParameter | start        | Start timestamp   | false    | string          |         |
| QueryParameter | end          | End timestamp     | false    | string          |         |
| QueryParameter | notification | Notification name | false    | string          |         |
| QueryParameter | sortField    | Sort field        | false    | string          |         |
| QueryParameter | sortOrder    | Sort order        | false    | string          |         |
| QueryParameter | take         | Limit param       | false    | integer (int32) |         |
| QueryParameter | skip         | Skip param        | false    | integer (int32) |         |
| QueryParameter | gridInterval | Grid interval     | false    | integer (int32) |         |

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Tags

- DeviceNotification

### Create notification

```
POST /device/{deviceGuid}/notification
```

#### Description

Creates notification

#### Parameters

| Type          | Name       | Description       | Required | Schema                    | Default |
| ------------- | ---------- | ----------------- | -------- | ------------------------- | ------- |
| PathParameter | deviceGuid | Device GUID       | true     | string                    |         |
| BodyParameter | body       | Notification body | true     | DeviceNotificationWrapper |         |

#### Responses

| HTTP Code | Description                           | Schema     |
| --------- | ------------------------------------- | ---------- |
| 400       | If request is malformed               | No Content |
| 403       | If device is not connected to network | No Content |
| 404       | If device not found                   | No Content |

#### Consumes

- application/json

#### Tags

- DeviceNotification

### Poll for notifications

```
GET /device/{deviceGuid}/notification/poll
```

#### Description

Polls for notifications based on provided parameters (long polling)

#### Parameters

| Type           | Name        | Description             | Required | Schema          | Default |
| -------------- | ----------- | ----------------------- | -------- | --------------- | ------- |
| PathParameter  | deviceGuid  | Device GUID             | true     | string          |         |
| QueryParameter | names       | Notification names      | false    | string          |         |
| QueryParameter | timestamp   | Timestamp to start from | false    | string          |         |
| QueryParameter | waitTimeout | Wait timeout            | false    | integer (int64) | 30      |
| BodyParameter  | body        |                         | false    | AsyncResponse   |         |

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Tags

- DeviceNotification

### Get notification

```
GET /device/{deviceGuid}/notification/{id}
```

#### Description

Returns notification by device guid and notification id

#### Parameters

| Type          | Name       | Description     | Required | Schema          | Default |
| ------------- | ---------- | --------------- | -------- | --------------- | ------- |
| PathParameter | deviceGuid | Device GUID     | true     | string          |         |
| PathParameter | id         | Notification id | true     | integer (int64) |         |

#### Responses

| HTTP Code | Description                         | Schema     |
| --------- | ----------------------------------- | ---------- |
| 404       | If device or notification not found | No Content |

#### Tags

- DeviceNotification

### Get device

```
GET /device/{id}
```

#### Description

Gets information about device.

#### Parameters

| Type          | Name | Description               | Required | Schema | Default |
| ------------- | ---- | ------------------------- | -------- | ------ | ------- |
| PathParameter | id   | Device unique identifier. | true     | string |         |

#### Responses

| HTTP Code | Description                                                                | Schema     |
| --------- | -------------------------------------------------------------------------- | ---------- |
| 200       | If successful, this method returns a Device resource in the response body. | Device     |
| 400       | If request is malformed                                                    | No Content |
| 401       | If request is not authorized                                               | No Content |
| 403       | If principal doesn't have permissions                                      | No Content |
| 404       | If device is not found                                                     | No Content |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- Device

### Register device

```
PUT /device/{id}
```

#### Description

Registers or updates a device. For initial device registration, only 'name' and 'deviceClass' properties are required.

#### Parameters

| Type          | Name | Description               | Required | Schema       | Default |
| ------------- | ---- | ------------------------- | -------- | ------------ | ------- |
| BodyParameter | body | Device body               | true     | DeviceUpdate |         |
| PathParameter | id   | Device unique identifier. | true     | string       |         |

#### Responses

| HTTP Code | Description                                                | Schema     |
| --------- | ---------------------------------------------------------- | ---------- |
| 400       | If request is malformed                                    | No Content |
| 401       | If request is not authorized                               | No Content |
| 204       | If successful, this method returns an empty response body. | No Content |
| 403       | If principal doesn't have permissions                      | No Content |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- Device

### Delete device

```
DELETE /device/{id}
```

#### Description

Deletes an existing device.

#### Parameters

| Type          | Name | Description               | Required | Schema | Default |
| ------------- | ---- | ------------------------- | -------- | ------ | ------- |
| PathParameter | id   | Device unique identifier. | true     | string |         |

#### Responses

| HTTP Code | Description                                                | Schema     |
| --------- | ---------------------------------------------------------- | ---------- |
| 400       | If request is malformed                                    | No Content |
| 401       | If request is not authorized                               | No Content |
| 204       | If successful, this method returns an empty response body. | No Content |
| 403       | If principal doesn't have permissions                      | No Content |
| 404       | If device is not found                                     | No Content |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- Device

### Get device's equipment

```
GET /device/{id}/equipment
```

#### Description

Gets current state of device equipment.  
The equipment state is tracked by framework and it could be updated by sending 'equipment' notification with the following parameters:  
equipment: equipment code  
parameters: current equipment state

#### Parameters

| Type          | Name | Description               | Required | Schema | Default |
| ------------- | ---- | ------------------------- | -------- | ------ | ------- |
| PathParameter | id   | Device unique identifier. | true     | string |         |

#### Responses

| HTTP Code | Description                                                                                    | Schema                |
| --------- | ---------------------------------------------------------------------------------------------- | --------------------- |
| 200       | If successful, this method returns an array of DeviceEquipment resources in the response body. | DeviceEquipment array |
| 400       | If request is malformed                                                                        | No Content            |
| 401       | If request is not authorized                                                                   | No Content            |
| 403       | If principal doesn't have permissions                                                          | No Content            |
| 404       | If device is not found                                                                         | No Content            |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- Device

### Get current state of equipment

```
GET /device/{id}/equipment/{code}
```

#### Description

Gets current state of device equipment by code.

#### Parameters

| Type          | Name | Description               | Required | Schema | Default |
| ------------- | ---- | ------------------------- | -------- | ------ | ------- |
| PathParameter | id   | Device unique identifier. | true     | string |         |
| PathParameter | code | Equipment code.           | true     | string |         |

#### Responses

| HTTP Code | Description                                                                         | Schema          |
| --------- | ----------------------------------------------------------------------------------- | --------------- |
| 200       | If successful, this method returns a DeviceEquipment resource in the response body. | DeviceEquipment |
| 401       | If request is not authorized                                                        | No Content      |
| 403       | If principal doesn't have permissions                                               | No Content      |
| 404       | If device or equipment is not found.                                                | No Content      |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- Device

### Get API info

```
GET /info
```

#### Description

Returns version of API, server timestamp and WebSocket base uri

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Consumes

- application/json

#### Tags

- ApiInfo

### Get oAuth configuration

```
GET /info/config/auth
```

#### Description

Returns configured identity providers

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Consumes

- application/json

#### Tags

- ApiInfo

### Get cluster configuration

```
GET /info/config/cluster
```

#### Description

Returns information about cluster (Kafka, Zookeeper etc.)

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Consumes

- application/json

#### Tags

- ApiInfo

### List networks

```
GET /network
```

#### Description

Gets list of device networks the client has access to.

#### Parameters

| Type           | Name        | Description                                     | Required | Schema           | Default |
| -------------- | ----------- | ----------------------------------------------- | -------- | ---------------- | ------- |
| QueryParameter | name        | Filter by network name.                         | false    | string           |         |
| QueryParameter | namePattern | Filter by network name pattern.                 | false    | string           |         |
| QueryParameter | sortField   | Result list sort field.                         | false    | enum (ID, Name)  |         |
| QueryParameter | sortOrder   | Result list sort order.                         | false    | enum (ASC, DESC) |         |
| QueryParameter | take        | Number of records to take from the result list. | false    | integer (int32)  | 20      |
| QueryParameter | skip        | Number of records to skip from the result list. | false    | integer (int32)  | 0       |

#### Responses

| HTTP Code | Description                                                                         | Schema        |
| --------- | ----------------------------------------------------------------------------------- | ------------- |
| 200       | If successful, this method returns array of Network resources in the response body. | Network array |
| 400       | If request parameters invalid                                                       | No Content    |
| 401       | If request is not authorized                                                        | No Content    |
| 403       | If principal doesn't have permissions                                               | No Content    |

#### Consumes

- application/json

#### Tags

- Network

### Create network

```
POST /network
```

#### Description

Creates new device network.

#### Parameters

| Type          | Name | Description  | Required | Schema  | Default |
| ------------- | ---- | ------------ | -------- | ------- | ------- |
| BodyParameter | body | Network body | true     | Network |         |

#### Responses

| HTTP Code | Description                                                                 | Schema     |
| --------- | --------------------------------------------------------------------------- | ---------- |
| 201       | If successful, this method returns a Network resource in the response body. | Network    |
| 400       | If request is malformed                                                     | No Content |
| 401       | If request is not authorized                                                | No Content |
| 403       | If principal doesn't have permissions                                       | No Content |

#### Consumes

- application/json

#### Tags

- Network

### Get network

```
GET /network/{id}
```

#### Description

Gets information about device network and its devices.

#### Parameters

| Type          | Name | Description         | Required | Schema          | Default |
| ------------- | ---- | ------------------- | -------- | --------------- | ------- |
| PathParameter | id   | Network identifier. | true     | integer (int64) |         |

#### Responses

| HTTP Code | Description                                                                 | Schema     |
| --------- | --------------------------------------------------------------------------- | ---------- |
| 200       | If successful, this method returns a Network resource in the response body. | Network    |
| 400       | If request is malformed                                                     | No Content |
| 401       | If request is not authorized                                                | No Content |
| 403       | If principal doesn't have permissions                                       | No Content |
| 404       | If network not found                                                        | No Content |

#### Consumes

- application/json

#### Tags

- Network

### Update network

```
PUT /network/{id}
```

#### Description

Updates an existing device network.

#### Parameters

| Type          | Name | Description         | Required | Schema          | Default |
| ------------- | ---- | ------------------- | -------- | --------------- | ------- |
| BodyParameter | body | Network body        | true     | NetworkUpdate   |         |
| PathParameter | id   | Network identifier. | true     | integer (int64) |         |

#### Responses

| HTTP Code | Description                                                | Schema     |
| --------- | ---------------------------------------------------------- | ---------- |
| 400       | If request is malformed                                    | No Content |
| 401       | If request is not authorized                               | No Content |
| 204       | If successful, this method returns an empty response body. | No Content |
| 403       | If principal doesn't have permissions                      | No Content |

#### Consumes

- application/json

#### Tags

- Network

### Delete network

```
DELETE /network/{id}
```

#### Description

Deletes an existing device network.

#### Parameters

| Type          | Name | Description         | Required | Schema          | Default |
| ------------- | ---- | ------------------- | -------- | --------------- | ------- |
| PathParameter | id   | Network identifier. | true     | integer (int64) |         |

#### Responses

| HTTP Code | Description                                                | Schema     |
| --------- | ---------------------------------------------------------- | ---------- |
| 401       | If request is not authorized                               | No Content |
| 204       | If successful, this method returns an empty response body. | No Content |
| 403       | If principal doesn't have permissions                      | No Content |
| 404       | If network not found                                       | No Content |

#### Consumes

- application/json

#### Tags

- Network

### List oAuth clients

```
GET /oauth/client
```

#### Parameters

| Type           | Name        | Description         | Required | Schema          | Default |
| -------------- | ----------- | ------------------- | -------- | --------------- | ------- |
| QueryParameter | name        | oAuth client name   | false    | string          |         |
| QueryParameter | namePattern | Name pattern        | false    | string          |         |
| QueryParameter | domain      | oAuth client domain | false    | string          |         |
| QueryParameter | oauthId     | oAuth client id     | false    | string          |         |
| QueryParameter | sortField   | Sort field          | false    | string          |         |
| QueryParameter | sortOrder   | Sort order          | false    | string          |         |
| QueryParameter | take        | Limit param         | false    | integer (int32) |         |
| QueryParameter | skip        | Skip param          | false    | integer (int32) |         |

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Tags

- OAuthClient

### Create oAuth client

```
POST /oauth/client
```

#### Parameters

| Type          | Name | Description       | Required | Schema      | Default |
| ------------- | ---- | ----------------- | -------- | ----------- | ------- |
| BodyParameter | body | oAuth client body | false    | OAuthClient |         |

#### Responses

| HTTP Code | Description             | Schema     |
| --------- | ----------------------- | ---------- |
| 400       | If request is malformed | No Content |

#### Tags

- OAuthClient

### Get oAuth client

```
GET /oauth/client/{id}
```

#### Description

Returns oAuth client by id

#### Parameters

| Type          | Name | Description     | Required | Schema          | Default |
| ------------- | ---- | --------------- | -------- | --------------- | ------- |
| PathParameter | id   | oAuth client id | true     | integer (int64) |         |

#### Responses

| HTTP Code | Description               | Schema     |
| --------- | ------------------------- | ---------- |
| 404       | If oAuth client not found | No Content |

#### Tags

- OAuthClient

### Update oAuth client

```
PUT /oauth/client/{id}
```

#### Parameters

| Type          | Name | Description       | Required | Schema            | Default |
| ------------- | ---- | ----------------- | -------- | ----------------- | ------- |
| PathParameter | id   | oAuth client id   | true     | integer (int64)   |         |
| BodyParameter | body | oAuth client body | false    | OAuthClientUpdate |         |

#### Responses

| HTTP Code | Description               | Schema     |
| --------- | ------------------------- | ---------- |
| 403       | If oAuth already exist    | No Content |
| 404       | If oAuth client not found | No Content |

#### Tags

- OAuthClient

### Delete oAuth client

```
DELETE /oauth/client/{id}
```

#### Parameters

| Type          | Name | Description     | Required | Schema          | Default |
| ------------- | ---- | --------------- | -------- | --------------- | ------- |
| PathParameter | id   | oAuth client id | true     | integer (int64) |         |

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Tags

- OAuthClient

### Access token request

```
POST /oauth2/token
```

#### Parameters

| Type              | Name        | Description       | Required | Schema | Default |
| ----------------- | ----------- | ----------------- | -------- | ------ | ------- |
| FormDataParameter | grant_type  | Grant type        | true     | string |         |
| FormDataParameter | code        | Code              | true     | string |         |
| FormDataParameter | redirectUri | Redirect Uri      | true     | string |         |
| FormDataParameter | client_id   | Client Id         | true     | string |         |
| FormDataParameter | scope       | Scope             | true     | string |         |
| FormDataParameter | username    | User name (Login) | true     | string |         |
| FormDataParameter | password    | Password          | true     | string |         |

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Consumes

- application/x-www-form-urlencoded

#### Tags

- Authentication

### List users

```
GET /user
```

#### Description

Gets list of users.

#### Parameters

| Type           | Name         | Description                                                         | Required | Schema           | Default |
| -------------- | ------------ | ------------------------------------------------------------------- | -------- | ---------------- | ------- |
| QueryParameter | login        | Filter by user login.                                               | false    | string           |         |
| QueryParameter | loginPattern | Filter by user login pattern.                                       | false    | string           |         |
| QueryParameter | role         | Filter by user role. 0 is Administrator, 1 is Client.               | false    | integer (int32)  |         |
| QueryParameter | status       | Filter by user status. 0 is Active, 1 is Locked Out, 2 is Disabled. | false    | integer (int32)  |         |
| QueryParameter | sortField    | Result list sort field.                                             | false    | enum (ID, Login) |         |
| QueryParameter | sortOrder    | Result list sort order. Available values are ASC and DESC.          | false    | enum (ASC, DESC) |         |
| QueryParameter | take         | Number of records to take from the result list.                     | false    | integer (int32)  | 20      |
| QueryParameter | skip         | Number of records to skip from the result list.                     | false    | integer (int32)  | 0       |

#### Responses

| HTTP Code | Description                                                                      | Schema     |
| --------- | -------------------------------------------------------------------------------- | ---------- |
| 200       | If successful, this method returns array of User resources in the response body. | User array |
| 400       | If request parameters invalid                                                    | No Content |
| 401       | If request is not authorized                                                     | No Content |
| 403       | If principal doesn't have permissions                                            | No Content |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- User

### Create user

```
POST /user
```

#### Description

Creates new user.

#### Parameters

| Type          | Name | Description | Required | Schema     | Default |
| ------------- | ---- | ----------- | -------- | ---------- | ------- |
| BodyParameter | body | User body   | true     | UserUpdate |         |

#### Responses

| HTTP Code | Description                                                              | Schema     |
| --------- | ------------------------------------------------------------------------ | ---------- |
| 200       | If successful, this method returns a User resource in the response body. | User       |
| 400       | If request is malformed                                                  | No Content |
| 401       | If request is not authorized                                             | No Content |
| 403       | If principal doesn't have permissions                                    | No Content |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- User

### Get current user

```
GET /user/current
```

#### Description

Get information about the current user.

#### Responses

| HTTP Code | Description                                                              | Schema     |
| --------- | ------------------------------------------------------------------------ | ---------- |
| 200       | If successful, this method returns a User resource in the response body. | User       |
| 401       | If request is not authorized                                             | No Content |
| 403       | If principal doesn't have permissions                                    | No Content |
| 409       | If user is not signed in                                                 | No Content |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- User

### Update current user

```
PUT /user/current
```

#### Description

Updates an existing user.  
Only administrators are allowed to update any property of any user. User-level accounts can only change their own password in case:

1. They already have a password.
2. They provide a valid current password in the 'oldPassword' property.

#### Parameters

| Type          | Name | Description | Required | Schema     | Default |
| ------------- | ---- | ----------- | -------- | ---------- | ------- |
| BodyParameter | body | User body   | true     | UserUpdate |         |

#### Responses

| HTTP Code | Description                                                | Schema     |
| --------- | ---------------------------------------------------------- | ---------- |
| 400       | If request is malformed                                    | No Content |
| 401       | If request is not authorized                               | No Content |
| 204       | If successful, this method returns an empty response body. | No Content |
| 403       | If principal doesn't have permissions                      | No Content |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- User

### Get user

```
GET /user/{id}
```

#### Description

Gets information about user and its assigned networks.  
Only administrators are allowed to get information about any user. User-level accounts can only retrieve information about themselves.

#### Parameters

| Type          | Name | Description      | Required | Schema          | Default |
| ------------- | ---- | ---------------- | -------- | --------------- | ------- |
| PathParameter | id   | User identifier. | true     | integer (int64) |         |

#### Responses

| HTTP Code | Description                                                              | Schema     |
| --------- | ------------------------------------------------------------------------ | ---------- |
| 200       | If successful, this method returns a User resource in the response body. | User       |
| 400       | If request is malformed                                                  | No Content |
| 401       | If request is not authorized                                             | No Content |
| 403       | If principal doesn't have permissions                                    | No Content |
| 404       | If user is not found                                                     | No Content |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- User

### Update user

```
PUT /user/{id}
```

#### Parameters

| Type          | Name | Description      | Required | Schema          | Default |
| ------------- | ---- | ---------------- | -------- | --------------- | ------- |
| BodyParameter | body | User body        | true     | UserUpdate      |         |
| PathParameter | id   | User identifier. | true     | integer (int64) |         |

#### Responses

| HTTP Code | Description       | Schema     |
| --------- | ----------------- | ---------- |
| 404       | If user not found | No Content |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- User

### Delete user

```
DELETE /user/{id}
```

#### Description

Deletes an existing user.

#### Parameters

| Type          | Name | Description      | Required | Schema          | Default |
| ------------- | ---- | ---------------- | -------- | --------------- | ------- |
| PathParameter | id   | User identifier. | true     | integer (int64) |         |

#### Responses

| HTTP Code | Description                                                | Schema     |
| --------- | ---------------------------------------------------------- | ---------- |
| 401       | If request is not authorized                               | No Content |
| 204       | If successful, this method returns an empty response body. | No Content |
| 403       | If principal doesn't have permissions                      | No Content |
| 404       | If access key is not found                                 | No Content |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- User

### Get user's network

```
GET /user/{id}/network/{networkId}
```

#### Description

Gets information about user/network association.

#### Parameters

| Type          | Name      | Description         | Required | Schema          | Default |
| ------------- | --------- | ------------------- | -------- | --------------- | ------- |
| PathParameter | id        | User identifier.    | true     | integer (int64) |         |
| PathParameter | networkId | Network identifier. | true     | integer (int64) |         |

#### Responses

| HTTP Code | Description                                                                 | Schema     |
| --------- | --------------------------------------------------------------------------- | ---------- |
| 200       | If successful, this method returns a Network resource in the response body. | Network    |
| 401       | If request is not authorized                                                | No Content |
| 403       | If principal doesn't have permissions                                       | No Content |
| 404       | If user or network not found                                                | No Content |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- User

### Assign network

```
PUT /user/{id}/network/{networkId}
```

#### Description

Associates network with the user.

#### Parameters

| Type          | Name      | Description         | Required | Schema          | Default |
| ------------- | --------- | ------------------- | -------- | --------------- | ------- |
| PathParameter | id        | User identifier.    | true     | integer (int64) |         |
| PathParameter | networkId | Network identifier. | true     | integer (int64) |         |

#### Responses

| HTTP Code | Description                                                | Schema     |
| --------- | ---------------------------------------------------------- | ---------- |
| 401       | If request is not authorized                               | No Content |
| 204       | If successful, this method returns an empty response body. | No Content |
| 403       | If principal doesn't have permissions                      | No Content |
| 404       | If user or network not found                               | No Content |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- User

### Unassign network

```
DELETE /user/{id}/network/{networkId}
```

#### Description

Removes association between network and user.

#### Parameters

| Type          | Name      | Description         | Required | Schema          | Default |
| ------------- | --------- | ------------------- | -------- | --------------- | ------- |
| PathParameter | id        | User identifier.    | true     | integer (int64) |         |
| PathParameter | networkId | Network identifier. | true     | integer (int64) |         |

#### Responses

| HTTP Code | Description                                                | Schema     |
| --------- | ---------------------------------------------------------- | ---------- |
| 401       | If request is not authorized                               | No Content |
| 204       | If successful, this method returns an empty response body. | No Content |
| 403       | If principal doesn't have permissions                      | No Content |
| 404       | If user or network not found.                              | No Content |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- User

### List access keys

```
GET /user/{userId}/accesskey
```

#### Description

Gets list of access keys and their permissions.

#### Parameters

| Type           | Name         | Description                                                                         | Required | Schema           | Default |
| -------------- | ------------ | ----------------------------------------------------------------------------------- | -------- | ---------------- | ------- |
| PathParameter  | userId       | User identifier. Use the 'current' keyword to list access keys of the current user. | true     | string           |         |
| QueryParameter | label        | Filter by access key label.                                                         | false    | string           |         |
| QueryParameter | labelPattern | Filter by access key label pattern.                                                 | false    | string           |         |
| QueryParameter | type         | Filter by access key type.                                                          | false    | integer (int32)  |         |
| QueryParameter | sortField    | Result list sort field.                                                             | false    | enum (ID, Label) |         |
| QueryParameter | sortOrder    | Result list sort order.                                                             | false    | enum (ASC, DESC) |         |
| QueryParameter | take         | Number of records to take from the result list.                                     | false    | integer (int32)  | 20      |
| QueryParameter | skip         | Number of records to skip from the result list.                                     | false    | integer (int32)  | 0       |

#### Responses

| HTTP Code | Description                                                                           | Schema          |
| --------- | ------------------------------------------------------------------------------------- | --------------- |
| 200       | If successful, this method returns array of AccessKey resources in the response body. | AccessKey array |
| 400       | If request parameters invalid                                                         | No Content      |
| 401       | If request is not authorized                                                          | No Content      |
| 403       | If principal doesn't have permissions                                                 | No Content      |
| 404       | If user with given userId is not found                                                | No Content      |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- AccessKey

### Create Access key

```
POST /user/{userId}/accesskey
```

#### Description

Creates new access key.

#### Parameters

| Type          | Name   | Description                                                                           | Required | Schema    | Default |
| ------------- | ------ | ------------------------------------------------------------------------------------- | -------- | --------- | ------- |
| PathParameter | userId | User identifier. Use the 'current' keyword to create access key for the current user. | true     | string    |         |
| BodyParameter | body   | Access Key Body                                                                       | true     | AccessKey |         |

#### Responses

| HTTP Code | Description                                                                   | Schema     |
| --------- | ----------------------------------------------------------------------------- | ---------- |
| 201       | If successful, this method returns a AccessKey resource in the response body. | AccessKey  |
| 400       | If request is malformed                                                       | No Content |
| 401       | If request is not authorized                                                  | No Content |
| 403       | If principal doesn't have permissions                                         | No Content |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- AccessKey

### Get user's access key

```
GET /user/{userId}/accesskey/{id}
```

#### Description

Gets information about access key and its permissions.

#### Parameters

| Type          | Name   | Description                                                                       | Required | Schema          | Default |
| ------------- | ------ | --------------------------------------------------------------------------------- | -------- | --------------- | ------- |
| PathParameter | userId | User identifier. Use the 'current' keyword to get access key of the current user. | true     | string          |         |
| PathParameter | id     | Access key identifier.                                                            | true     | integer (int64) |         |

#### Responses

| HTTP Code | Description                                                                   | Schema     |
| --------- | ----------------------------------------------------------------------------- | ---------- |
| 200       | If successful, this method returns a AccessKey resource in the response body. | AccessKey  |
| 400       | If request is malformed                                                       | No Content |
| 401       | If request is not authorized                                                  | No Content |
| 403       | If principal doesn't have permissions                                         | No Content |
| 404       | If access key is not found                                                    | No Content |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- AccessKey

### Update Access key

```
PUT /user/{userId}/accesskey/{id}
```

#### Description

Updates an existing access key.

#### Parameters

| Type          | Name   | Description                                                                          | Required | Schema          | Default |
| ------------- | ------ | ------------------------------------------------------------------------------------ | -------- | --------------- | ------- |
| PathParameter | userId | User identifier. Use the 'current' keyword to update access key of the current user. | true     | string          |         |
| PathParameter | id     | Access key identifier.                                                               | true     | integer (int64) |         |
| BodyParameter | body   | Access Key Body                                                                      | true     | AccessKeyUpdate |         |

#### Responses

| HTTP Code | Description                                                | Schema     |
| --------- | ---------------------------------------------------------- | ---------- |
| 400       | If request is malformed                                    | No Content |
| 401       | If request is not authorized                               | No Content |
| 204       | If successful, this method returns an empty response body. | No Content |
| 403       | If principal doesn't have permissions                      | No Content |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- AccessKey

### Delete Access key

```
DELETE /user/{userId}/accesskey/{id}
```

#### Description

Deletes an existing access key.

#### Parameters

| Type          | Name   | Description                                                                          | Required | Schema          | Default |
| ------------- | ------ | ------------------------------------------------------------------------------------ | -------- | --------------- | ------- |
| PathParameter | userId | User identifier. Use the 'current' keyword to delete access key of the current user. | true     | string          |         |
| PathParameter | id     | Access key identifier.                                                               | true     | integer (int64) |         |

#### Responses

| HTTP Code | Description                                                | Schema     |
| --------- | ---------------------------------------------------------- | ---------- |
| 401       | If request is not authorized                               | No Content |
| 204       | If successful, this method returns an empty response body. | No Content |
| 403       | If principal doesn't have permissions                      | No Content |
| 404       | If access key is not found                                 | No Content |

#### Consumes

- application/json

#### Produces

- application/json

#### Tags

- AccessKey

### List oAuth grants

```
GET /user/{userId}/oauth/grant
```

#### Description

Returns list of oAuth grants for user

#### Parameters

| Type           | Name          | Description     | Required | Schema          | Default |
| -------------- | ------------- | --------------- | -------- | --------------- | ------- |
| PathParameter  | userId        | User Id         | true     | string          |         |
| QueryParameter | start         | Start timestamp | false    | string          |         |
| QueryParameter | end           | End timestamp   | false    | string          |         |
| QueryParameter | clientOAuthId | Client oAuth id | false    | string          |         |
| QueryParameter | type          | Type            | false    | string          |         |
| QueryParameter | scope         | Scope           | false    | string          |         |
| QueryParameter | redirectUri   | Redirect uri    | false    | string          |         |
| QueryParameter | accessType    | Access type     | false    | string          |         |
| QueryParameter | sortField     | Sort field      | false    | string          |         |
| QueryParameter | sortOrder     | Sort order      | false    | string          |         |
| QueryParameter | take          | Limit param     | false    | integer (int32) |         |
| QueryParameter | skip          | Skip param      | false    | integer (int32) |         |

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Tags

- OAuthGrant

### Create oAuth grant

```
POST /user/{userId}/oauth/grant
```

#### Parameters

| Type          | Name   | Description | Required | Schema     | Default |
| ------------- | ------ | ----------- | -------- | ---------- | ------- |
| PathParameter | userId | User Id     | true     | string     |         |
| BodyParameter | body   | Grant body  | true     | OAuthGrant |         |

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Tags

- OAuthGrant

### Get oAuth grant

```
GET /user/{userId}/oauth/grant/{id}
```

#### Description

Returns oAuth grant by user and id

#### Parameters

| Type          | Name   | Description | Required | Schema          | Default |
| ------------- | ------ | ----------- | -------- | --------------- | ------- |
| PathParameter | userId | User Id     | true     | string          |         |
| PathParameter | id     | Grant Id    | true     | integer (int64) |         |

#### Responses

| HTTP Code | Description        | Schema     |
| --------- | ------------------ | ---------- |
| 404       | If grant not found | No Content |

#### Tags

- OAuthGrant

### Update oAuth grant

```
PUT /user/{userId}/oauth/grant/{id}
```

#### Parameters

| Type          | Name   | Description | Required | Schema           | Default |
| ------------- | ------ | ----------- | -------- | ---------------- | ------- |
| PathParameter | userId | User Id     | true     | string           |         |
| PathParameter | id     | Grant Id    | true     | integer (int64)  |         |
| BodyParameter | body   | Grant body  | true     | OAuthGrantUpdate |         |

#### Responses

| HTTP Code | Description        | Schema     |
| --------- | ------------------ | ---------- |
| 404       | If grant not found | No Content |

#### Tags

- OAuthGrant

### Delete oAuth grant

```
DELETE /user/{userId}/oauth/grant/{id}
```

#### Parameters

| Type          | Name   | Description | Required | Schema          | Default |
| ------------- | ------ | ----------- | -------- | --------------- | ------- |
| PathParameter | userId | User Id     | true     | string          |         |
| PathParameter | id     | Grant Id    | true     | integer (int64) |         |

#### Responses

| HTTP Code | Description          | Schema     |
| --------- | -------------------- | ---------- |
| default   | successful operation | No Content |

#### Tags

- OAuthGrant
