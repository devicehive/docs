---
title: "JWT Tokens explanation"
slug: "jwt-tockens-explanation"
excerpt: ""
hidden: true
metadata: 
  image: []
  robots: "index"
createdAt: "Mon Jan 15 2018 14:44:05 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Feb 18 2025 13:02:59 GMT+0000 (Coordinated Universal Time)"
---
{  
   "payload": {  
      "u": 17248,  
      "a": [  
         2,  
         3,  
         4,  
         5,  
         6,  
         7,  
         8,  
         9,  
         10,  
         11,  
         15  
      ],  
      "n": [  
          "12342"  
      ],  
      "dt": [  
         "*"  
      ],  
      "e": 1505811340258,  
      "t": 1  
   }  
}

ANY: 0  
NONE: 1  
GET_NETWORK: 2  
GET_DEVICE: 3  
GET_DEVICE_NOTIFICATION: 4  
GET_DEVICE_COMMAND: 5  
REGISTER_DEVICE: 6  
CREATE_DEVICE_COMMAND: 7  
UPDATE_DEVICE_COMMAND: 8  
CREATE_DEVICE_NOTIFICATION: 9  
GET_CURRENT_USER: 10  
UPDATE_CURRENT_USER: 11  
MANAGE_USER: 12  
MANAGE_CONFIGURATION: 13  
MANAGE_NETWORK: 14  
MANAGE_TOKEN: 15

USER_ID: u  
ACTIONS: a  
NETWORK_IDS: n  
DEVICE_TYPE_IDS: dt  
EXPIRATION: e  
TOKEN_TYPE: t (1 for ACCESS, 0 for REFRESH)
