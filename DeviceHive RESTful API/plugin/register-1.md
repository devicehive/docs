---
title: "register"
slug: "register-1"
excerpt: ""
hidden: false
metadata: 
  image: []
  robots: "index"
createdAt: "Wed Nov 15 2017 16:56:46 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Jan 23 2018 10:27:58 GMT+0000 (Coordinated Universal Time)"
---
Registers new plugin.

## Request

**HTTP Request**

```text
POST /plugin/register
```

**Parameters**

| Parameter Name        | Required | Type     | Description                                                                                                                                                                                                                             |
| :-------------------- | :------- | :------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| deviceIds             | No       | string   | Comma-separated list of device ids for subscription. If not specified the devices available to current user.                                                                                                                            |
| networkIds            | No       | string   | Comma-separated list of network ids for subscription. If not specified the networks available to current user.                                                                                                                          |
| names                 | No       | string   | Comma-separated list of command/notification names for subscription.                                                                                                                                                                    |
| timestamp             | No       | datetime | UTC datetime (yyyy-MM-dd'T'HH:mm:ss.SSS [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)) of the last received  / last updated (if returnUpdatedCommands selected) command. If not specified, the server's datetime is taken instead. |
| returnCommands        | No       | boolean  | Checks if subscription should return commands. If not specified, default value is true.                                                                                                                                                 |
| returnUpdatedCommands | No       | boolean  | Checks if subscription should return updated commands. If not specified, default value is false.                                                                                                                                        |
| returnNotifications   | No       | boolean  | Checks if subscription should return notifications. If not specified, default value is false.                                                                                                                                           |

**Authorization**

Access JSON Web Token (ManagePlugin)

**Request Body**

In the request body, supply a [Plugin](doc:plugin) resource.

| Property Name | Required | Type   | Description                 |
| :------------ | :------- | :----- | :-------------------------- |
| name          | Yes      | string | Plugin name                 |
| description   | Yes      | string | Plugin description          |
| parameters    | No       | object | Json object with parameters |

## Response

If successful, this method returns the following resource in the response body.

```text
{
  "accessToken": {string},
  "refreshToken": {string},
  "proxyEndpoint": {string}
}
```

**Parameters**

| Property Name | Type   | Description                                                                        |
| :------------ | :----- | :--------------------------------------------------------------------------------- |
| accessToken   | string | Plugin access token to connect to ws-kafka-proxy with permissions to plugin topic  |
| refreshToken  | string | Plugin refresh token to connect to ws-kafka-proxy with permissions to plugin topic |
| proxyEndpoint | string | Endpoint to connect to ws-kafka-proxy                                              |
