---
title: "Definitions"
slug: "websockets"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Fri Jul 24 2015 05:50:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
### Set

| Name  | Description | Required | Schema  | Default |
| ----- | ----------- | -------- | ------- | ------- |
| empty |             | false    | boolean | false   |

### User

| Name          | Description | Required | Schema                                       | Default |
| ------------- | ----------- | -------- | -------------------------------------------- | ------- |
| id            |             | false    | integer (int64)                              |         |
| login         |             | true     | string                                       |         |
| passwordHash  |             | false    | string                                       |         |
| passwordSalt  |             | false    | string                                       |         |
| loginAttempts |             | false    | integer (int32)                              |         |
| role          |             | false    | enum (ADMIN, CLIENT)                         |         |
| status        |             | false    | enum (ACTIVE, LOCKED_OUT, DISABLED, DELETED) |         |
| networks      |             | false    | Set                                          |         |
| lastLogin     |             | false    | string (date-time)                           |         |
| googleLogin   |             | false    | string                                       |         |
| facebookLogin |             | false    | string                                       |         |
| githubLogin   |             | false    | string                                       |         |
| entityVersion |             | false    | integer (int64)                              |         |
| data          |             | false    | JsonStringWrapper                            |         |
| admin         |             | false    | boolean                                      | false   |

### EquipmentUpdate

| Name | Description | Required | Schema          | Default |
| ---- | ----------- | -------- | --------------- | ------- |
| id   |             | false    | integer (int64) |         |
| name |             | false    | NullableWrapper |         |
| code |             | false    | NullableWrapper |         |
| type |             | false    | NullableWrapper |         |
| data |             | false    | NullableWrapper |         |

### OAuthGrantUpdate

| Name        | Description | Required | Schema          | Default |
| ----------- | ----------- | -------- | --------------- | ------- |
| id          |             | false    | integer (int64) |         |
| client      |             | false    | NullableWrapper |         |
| type        |             | false    | NullableWrapper |         |
| accessType  |             | false    | NullableWrapper |         |
| redirectUri |             | false    | NullableWrapper |         |
| scope       |             | false    | NullableWrapper |         |
| networkIds  |             | false    | NullableWrapper |         |

### OAuthClient

| Name        | Description | Required | Schema          | Default |
| ----------- | ----------- | -------- | --------------- | ------- |
| id          |             | false    | integer (int64) |         |
| name        |             | true     | string          |         |
| domain      |             | true     | string          |         |
| subnet      |             | false    | string          |         |
| redirectUri |             | true     | string          |         |
| oauthId     |             | true     | string          |         |
| oauthSecret |             | true     | string          |         |

### DeviceClass

| Name           | Description | Required | Schema            | Default |
| -------------- | ----------- | -------- | ----------------- | ------- |
| id             |             | false    | integer (int64)   |         |
| name           |             | true     | string            |         |
| version        |             | true     | string            |         |
| offlineTimeout |             | false    | integer (int32)   |         |
| data           |             | false    | JsonStringWrapper |         |
| entityVersion  |             | false    | integer (int64)   |         |
| equipment      |             | false    | Equipment array   |         |
| permanent      |             | false    | boolean           | false   |

### AccessKeyRequest

| Name         | Description | Required | Schema | Default |
| ------------ | ----------- | -------- | ------ | ------- |
| providerName |             | false    | string |         |
| code         |             | false    | string |         |
| redirectUri  |             | false    | string |         |
| accessToken  |             | false    | string |         |
| login        |             | false    | string |         |
| password     |             | false    | string |         |

### AccessKeyPermission

| Name             | Description | Required | Schema                | Default |
| ---------------- | ----------- | -------- | --------------------- | ------- |
| id               |             | false    | integer (int64)       |         |
| domains          |             | false    | JsonStringWrapper     |         |
| subnets          |             | false    | JsonStringWrapper     |         |
| actions          |             | false    | JsonStringWrapper     |         |
| networkIds       |             | false    | JsonStringWrapper     |         |
| deviceGuids      |             | false    | JsonStringWrapper     |         |
| entityVersion    |             | false    | integer (int64)       |         |
| deviceGuidsAsSet |             | false    | string array          |         |
| networkIdsAsSet  |             | false    | integer (int64) array |         |
| subnetsAsSet     |             | false    | Subnet array          |         |
| domainsAsSet     |             | false    | string array          |         |
| actionsAsSet     |             | false    | string array          |         |

### JsonStringWrapper

| Name       | Description | Required | Schema | Default |
| ---------- | ----------- | -------- | ------ | ------- |
| jsonString |             | false    | string |         |

### DeviceClassUpdate

| Name           | Description | Required | Schema            | Default |
| -------------- | ----------- | -------- | ----------------- | ------- |
| id             |             | false    | integer (int64)   |         |
| name           |             | false    | string            |         |
| version        |             | false    | string            |         |
| offlineTimeout |             | false    | integer (int32)   |         |
| data           |             | false    | JsonStringWrapper |         |
| equipment      |             | false    | NullableWrapper   |         |
| permanent      |             | false    | NullableWrapper   |         |

### Network

| Name          | Description | Required | Schema          | Default |
| ------------- | ----------- | -------- | --------------- | ------- |
| id            |             | false    | integer (int64) |         |
| key           |             | false    | string          |         |
| name          |             | true     | string          |         |
| description   |             | false    | string          |         |
| users         |             | false    | User array      |         |
| devices       |             | false    | Set             |         |
| entityVersion |             | false    | integer (int64) |         |

### OAuthGrant

| Name            | Description | Required | Schema                       | Default |
| --------------- | ----------- | -------- | ---------------------------- | ------- |
| id              |             | false    | integer (int64)              |         |
| timestamp       |             | false    | string (date-time)           |         |
| authCode        |             | false    | string                       |         |
| client          |             | true     | OAuthClient                  |         |
| accessKey       |             | true     | AccessKey                    |         |
| user            |             | true     | User                         |         |
| type            |             | false    | enum (CODE, TOKEN, PASSWORD) |         |
| accessType      |             | false    | enum (ONLINE, OFFLINE)       |         |
| redirectUri     |             | true     | string                       |         |
| scope           |             | true     | string                       |         |
| networkIds      |             | false    | JsonStringWrapper            |         |
| entityVersion   |             | false    | integer (int64)              |         |
| networkIdsAsSet |             | false    | integer (int64) array        |         |

### AccessKey

| Name           | Description | Required | Schema                         | Default |
| -------------- | ----------- | -------- | ------------------------------ | ------- |
| id             |             | false    | integer (int64)                |         |
| label          |             | true     | string                         |         |
| key            |             | true     | string                         |         |
| user           |             | true     | User                           |         |
| expirationDate |             | false    | string (date-time)             |         |
| type           |             | false    | enum (DEFAULT, SESSION, OAUTH) |         |
| permissions    |             | true     | AccessKeyPermission array      |         |
| entityVersion  |             | false    | integer (int64)                |         |

### OAuthClientUpdate

| Name        | Description | Required | Schema          | Default |
| ----------- | ----------- | -------- | --------------- | ------- |
| id          |             | false    | integer (int64) |         |
| name        |             | false    | NullableWrapper |         |
| domain      |             | false    | NullableWrapper |         |
| subnet      |             | false    | NullableWrapper |         |
| redirectUri |             | false    | NullableWrapper |         |
| oauthId     |             | false    | NullableWrapper |         |

### DeviceCommandWrapper

| Name       | Description | Required | Schema            | Default |
| ---------- | ----------- | -------- | ----------------- | ------- |
| command    |             | false    | string            |         |
| parameters |             | false    | JsonStringWrapper |         |
| lifetime   |             | false    | integer (int32)   |         |
| status     |             | false    | string            |         |
| result     |             | false    | JsonStringWrapper |         |

### Device

| Name          | Description | Required | Schema            | Default |
| ------------- | ----------- | -------- | ----------------- | ------- |
| id            |             | false    | integer (int64)   |         |
| guid          |             | true     | string            |         |
| key           |             | true     | string            |         |
| name          |             | true     | string            |         |
| status        |             | false    | string            |         |
| data          |             | false    | JsonStringWrapper |         |
| network       |             | false    | Network           |         |
| deviceClass   |             | true     | DeviceClass       |         |
| entityVersion |             | false    | integer (int64)   |         |
| blocked       |             | false    | boolean           | false   |

### DeviceNotificationWrapper

| Name         | Description | Required | Schema            | Default |
| ------------ | ----------- | -------- | ----------------- | ------- |
| notification |             | false    | string            |         |
| parameters   |             | false    | JsonStringWrapper |         |

### NullableWrapper

| Name  | Description | Required | Schema  | Default |
| ----- | ----------- | -------- | ------- | ------- |
| value |             | false    | boolean | false   |

### NetworkUpdate

| Name        | Description | Required | Schema          | Default |
| ----------- | ----------- | -------- | --------------- | ------- |
| id          |             | false    | integer (int64) |         |
| key         |             | false    | NullableWrapper |         |
| name        |             | false    | NullableWrapper |         |
| description |             | false    | NullableWrapper |         |

### Equipment

| Name          | Description | Required | Schema            | Default |
| ------------- | ----------- | -------- | ----------------- | ------- |
| id            |             | false    | integer (int64)   |         |
| name          |             | true     | string            |         |
| code          |             | true     | string            |         |
| type          |             | true     | string            |         |
| data          |             | false    | JsonStringWrapper |         |
| entityVersion |             | false    | integer (int64)   |         |

### AccessKeyUpdate

| Name           | Description | Required | Schema                         | Default |
| -------------- | ----------- | -------- | ------------------------------ | ------- |
| label          |             | false    | NullableWrapper                |         |
| expirationDate |             | false    | NullableWrapper                |         |
| permissions    |             | false    | NullableWrapper                |         |
| type           |             | false    | NullableWrapper                |         |
| typeEnum       |             | false    | enum (DEFAULT, SESSION, OAUTH) |         |

### UserUpdate

| Name          | Description | Required | Schema                                       | Default |
| ------------- | ----------- | -------- | -------------------------------------------- | ------- |
| login         |             | false    | NullableWrapper                              |         |
| role          |             | false    | NullableWrapper                              |         |
| status        |             | false    | NullableWrapper                              |         |
| password      |             | false    | NullableWrapper                              |         |
| oldPassword   |             | false    | NullableWrapper                              |         |
| googleLogin   |             | false    | NullableWrapper                              |         |
| facebookLogin |             | false    | NullableWrapper                              |         |
| githubLogin   |             | false    | NullableWrapper                              |         |
| data          |             | false    | NullableWrapper                              |         |
| roleEnum      |             | false    | enum (ADMIN, CLIENT)                         |         |
| statusEnum    |             | false    | enum (ACTIVE, LOCKED_OUT, DISABLED, DELETED) |         |

### DeviceEquipment

| Name          | Description | Required | Schema             | Default |
| ------------- | ----------- | -------- | ------------------ | ------- |
| id            |             | false    | integer (int64)    |         |
| code          |             | true     | string             |         |
| timestamp     |             | true     | string (date-time) |         |
| parameters    |             | false    | JsonStringWrapper  |         |
| device        |             | true     | Device             |         |
| entityVersion |             | false    | integer (int64)    |         |

### DeviceUpdate

| Name        | Description | Required | Schema            | Default |
| ----------- | ----------- | -------- | ----------------- | ------- |
| guid        |             | false    | string            |         |
| key         |             | false    | string            |         |
| name        |             | false    | string            |         |
| status      |             | false    | string            |         |
| data        |             | false    | JsonStringWrapper |         |
| network     |             | false    | Network           |         |
| deviceClass |             | false    | DeviceClassUpdate |         |
| blocked     |             | false    | boolean           | false   |

### Subnet

| Name        | Description | Required | Schema          | Default |
| ----------- | ----------- | -------- | --------------- | ------- |
| inetAddress |             | false    | InetAddress     |         |
| mask        |             | false    | integer (int32) |         |
| subnet      |             | false    | string          |         |

### AsyncResponse

| Name      | Description | Required | Schema  | Default |
| --------- | ----------- | -------- | ------- | ------- |
| done      |             | false    | boolean | false   |
| suspended |             | false    | boolean | false   |
| cancelled |             | false    | boolean | false   |

### InetAddress

| Name              | Description | Required | Schema       | Default |
| ----------------- | ----------- | -------- | ------------ | ------- |
| address           |             | false    | string array |         |
| hostAddress       |             | false    | string       |         |
| hostName          |             | false    | string       |         |
| canonicalHostName |             | false    | string       |         |
| anyLocalAddress   |             | false    | boolean      | false   |
| linkLocalAddress  |             | false    | boolean      | false   |
| loopbackAddress   |             | false    | boolean      | false   |
| mcglobal          |             | false    | boolean      | false   |
| mclinkLocal       |             | false    | boolean      | false   |
| mcnodeLocal       |             | false    | boolean      | false   |
| mcorgLocal        |             | false    | boolean      | false   |
| mcsiteLocal       |             | false    | boolean      | false   |
| multicastAddress  |             | false    | boolean      | false   |
| siteLocalAddress  |             | false    | boolean      | false   |
