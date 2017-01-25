# API Reference

All endpoints will resolve with the following host (domain) name/address:

`http://localhost:3000`


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Get All Users

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "method": "users.fetchUsers",
  "id": "1234"
}
```

```json-doc
"GET /api/users HTTP/1.1"
```

> The above command returns JSON structured like this:

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "result": [
    {
      "avatarFilename": "testing.jpeg",
      "createdAt": "2016-11-11T19:52:08.000Z",
      "email": "thingy1@gmail.com",
      "energy": 25,
      "fbId": "10207332672302279",
      "id": "6abd8d81-c24d-41a6-bee7-db49efd2c70d",
      "username": "catinthehat",
      "avatarURL": "https://s3.amazonaws.com/gotchuu/dev/users/avatars/testing.jpeg"
    },
    {
      "createdAt": "2016-08-01T20:59:37.000Z",
      "curAvatarId": "bdbcdcb3-163b-4ca0-b388-31b25db4e47b",
      "email": "integrationtesting@gmail.com",
      "energy": 13,
      "energyLastRegen": "2016-08-02T20:33:24.000Z",
      "fbId": "9000",
      "id": "d3b0a471-eb99-42a6-9d87-76299abfd64a",
      "location": {
        "latitude": 33.650928,
        "longitude": -117.714303
      },
      "username": "JumpNShoot",
      "avatarURL": null
    }
  ]
}
```

```json-doc
{
  "success": true,
  "result": [
    {
      "avatarFilename": "testing.jpeg",
      "createdAt": "2016-11-11T19:52:08.000Z",
      "email": "thingy1@gmail.com",
      "energy": 25,
      "fbId": "10207332672302279",
      "id": "6abd8d81-c24d-41a6-bee7-db49efd2c70d",
      "username": "catinthehat",
      "avatarURL": "https://s3.amazonaws.com/gotchuu/dev/users/avatars/testing.jpeg"
    },
    {
      "createdAt": "2016-08-01T20:59:37.000Z",
      "curAvatarId": "bdbcdcb3-163b-4ca0-b388-31b25db4e47b",
      "email": "integrationtesting@gmail.com",
      "energy": 13,
      "energyLastRegen": "2016-08-02T20:33:24.000Z",
      "fbId": "9000",
      "id": "d3b0a471-eb99-42a6-9d87-76299abfd64a",
      "location": {
        "latitude": 33.650928,
        "longitude": -117.714303
      },
      "username": "JumpNShoot",
      "avatarURL": null
    }
  ]
}
```

This endpoint retrieves all users.

### RPC Method Name
`users.fetchUsers`

### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Array | The result of the request. [userModel](#user) |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Get a Specific User

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "method": "users.fetchUser",
  "id": "1234",
  "params": {
    "userId": "specific-user-id"
  }
}
```

```json-doc
"GET /api/users/<specific-user-id> HTTP/1.1"
```

> The above command returns JSON structured like this:

```json
{
  "jsonrpc": "2.0",
  "id": "",
  "result": {
    "avatarFilename": "testing.jpeg",
    "createdAt": "2016-11-11T19:52:08.000Z",
    "email": "thingy1@gmail.com",
    "energy": 25,
    "fbId": "10207332672302279",
    "id": "6abd8d81-c24d-41a6-bee7-db49efd2c70d",
    "username": "catinthehat",
    "avatarURL": "https://s3.amazonaws.com/gotchuu/dev/users/avatars/testing.jpeg"
  }
}
```

```json-doc
{
  "success": true,
  "result": {
    "avatarFilename": "testing.jpeg",
    "createdAt": "2016-11-11T19:52:08.000Z",
    "email": "thingy1@gmail.com",
    "energy": 25,
    "fbId": "10207332672302279",
    "id": "6abd8d81-c24d-41a6-bee7-db49efd2c70d",
    "username": "catinthehat",
    "avatarURL": "https://s3.amazonaws.com/gotchuu/dev/users/avatars/testing.jpeg"
  }
}
```

This endpoint uses the userId passed to retrieve the details of a user.

### RPC Method Name
`users.fetchUser`

### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.fetchUser` |
| params | Object | A JSON object that contains the field `userId` with the string value of the unique user id. Example: ```{ "userId": "unique-user-id" }``` |

### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | The result of the request. [userModel](#user) |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Register/Create new User

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "method": "users.fetchUser",
  "id": "1234",
  "params": {
    "userData": {
      "fbId": "98723874623",
      "email": "testing@test.com",
      "username": "testingUser",
      "birthdate": "1988-01-14T00:00:00.000Z",
      "gender": 0,
      "city": "Huntington Beach"
    }
  }
}
```

```json-doc
"POST /api/users HTTP/1.1"
"Content-Type: application/json"
```

```json-doc
{
  "fbId": "98723874623",
  "email": "testing@test.com",
  "username": "testingUser",
  "birthdate": "1988-01-14T00:00:00.000Z",
  "gender": 0,
  "city": "Huntington Beach"
}
```

> The above command returns JSON structured like this:

```json
{
  "jsonrpc": "2.0",
  "id": "",
  "result": {
    "createdAt": "2016-11-11T19:52:08.000Z",
    "email": "testing@test.com",
    "fbId": "98723874623",
    "id": "6abd8d81-c24d-41a6-bee7-db49efd2c70d",
    "username": "testingUser",
    "gender": 0,
    "age": 28,
    "city": "Huntington Beach"
  }
}
```

```json-doc
{
  "success": true,
  "result": {
    "createdAt": "2016-11-11T19:52:08.000Z",
    "email": "testing@test.com",
    "fbId": "98723874623",
    "id": "6abd8d81-c24d-41a6-bee7-db49efd2c70d",
    "username": "testingUser",
    "gender": 0,
    "age": 28,
    "city": "Huntington Beach"
  }
}
```

This method is used to create a new user account.

### RPC Method Name
`users.registerUser`

### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.registerUser` |
| params | Object | Object that contains the field `userData` where the value is a JSON object that contains the userModel fields to save in the database |

### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | The result of the request. [userModel](#user) |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Update User Location

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "method": "users.updatePosition",
  "id": "1",
  "params": {
    "userId": "6abd8d81-c24d-41a6-bee7-db49efd2c70d",
    "location": {
      "latitude": 0,
      "longitude": 0
    }
  }
}
```

```json-doc
"PUT /api/users/6abd8d81-c24d-41a6-bee7-db49efd2c70d/updated-position HTTP/1.1"
"Content-Type: application/json"
```

```json-doc
{
  "location": {
    "latitude": 0,
    "longitude": 0
  }
}
```

> The above command returns JSON structured like this:

```json
{
  "jsonrpc": "2.0",
  "id": "1",
  "result": {
    "avatarFilename": "testing.jpeg",
    "createdAt": "2016-11-11T19:52:08.000Z",
    "email": "thingy1@gmail.com",
    "fbId": "10207332672302279",
    "id": "6abd8d81-c24d-41a6-bee7-db49efd2c70d",
    "location": {
      "latitude": 0,
      "longitude": 0
    },
    "username": "catinthehat"
  }
}
```

```json-doc
{
  "success": true,
  "result": {
    "avatarFilename": "testing.jpeg",
    "createdAt": "2016-11-11T19:52:08.000Z",
    "email": "thingy1@gmail.com",
    "fbId": "10207332672302279",
    "id": "6abd8d81-c24d-41a6-bee7-db49efd2c70d",
    "location": {
      "latitude": 0,
      "longitude": 0
    },
    "username": "catinthehat"
  }
}
```

This method accepts two parameters `userId` and `location`. The API uses the `userId` to find the user and the `location` information to setup the geospatial information in the database to support geospatial queries later. 

### RPC Method Name
`users.updatePosition`

### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.updatePosition` |
| params | Object | Object that contains the fields `userId` and `location` |

### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | The result of the request. [userModel](#user) |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Search for targets around User

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "method": "users.searchTargets",
  "id": "1",
  "params": {
    "userId": "6abd8d81-c24d-41a6-bee7-db49efd2c70d",
    "location": {
      "latitude": 0,
      "longitude": 0
    }
  }
}
```

```json-doc
"PUT /api/users/6abd8d81-c24d-41a6-bee7-db49efd2c70d/find-targets HTTP/1.1"
"Content-Type: application/json"
```

```json-doc
{
  "location": {
    "latitude": 0,
    "longitude": 0
  }
}
```

> The above command returns JSON structured like this:

```json
{
  "jsonrpc": "2.0",
  "id": "1",
  "result": [
    {
      "avatarFilename": "testing.jpeg",
      "createdAt": "2016-11-11T19:52:08.000Z",
      "email": "thingy1@gmail.com",
      "fbId": "10207332672302279",
      "id": "another-unique-user-id",
      "location": {
        "latitude": 0,
        "longitude": 0
      },
      "username": "blargasaurus"
    }
  ]
}
```

```json-doc
{
  "success": true,
  "result": [
    {
      "avatarFilename": "testing.jpeg",
      "createdAt": "2016-11-11T19:52:08.000Z",
      "email": "thingy1@gmail.com",
      "fbId": "10207332672302279",
      "id": "another-unique-user-id",
      "location": {
        "latitude": 0,
        "longitude": 0
      },
      "username": "blargasaurus"
    }
  ]
}
```

This method will serve two purposes; it will require a location object with the latitude and longitude and update the calling user's location, and after this is successful, the API will run a geospatial query using this new geopoint location and a set radius to find any users in the database within the area of the calling user. 

<aside class="notice">This method will omit returning the calling user's object</aside>

### RPC Method Name
`users.searchTargets`

### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.searchTargets` |
| params | Object | Object that contains the fields `userId` and `location` |

### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Array | The result of the request. Array of [userModels](#user) |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Login using Facebook

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "method": "users.loginFB",
  "id": "1",
  "params": {
    "body": {
      "access_token": "access-token-retrieved-from-successful-client-login"
    }
  }
}
```

```json-doc
"POST /api/login/facebook HTTP/1.1"
```

```json-doc
{
  "access_token": "access-token-retrieved-from-successful-client-login"
}
```

> The following is a successful login

```json
{
  "jsonrpc": "2.0",
  "id": "1",
  "result": {
    "avatarFilename": "testing.jpeg",
    "createdAt": "2016-11-11T19:52:08.000Z",
    "email": "thingy1@gmail.com",
    "fbId": "10207332672302279",
    "id": "another-unique-user-id",
    "location": {
      "latitude": 0,
      "longitude": 0
    },
    "username": "blargasaurus"
  }
}
```

```json-doc
{
  "success": true,
  "result": {
    "avatarFilename": "testing.jpeg",
    "createdAt": "2016-11-11T19:52:08.000Z",
    "email": "thingy1@gmail.com",
    "fbId": "10207332672302279",
    "id": "another-unique-user-id",
    "location": {
      "latitude": 0,
      "longitude": 0
    },
    "username": "blargasaurus"
  }
}
```

> The following result is if we have a successful token verification but no user exists in the system with the Facebook Id

```json
{
  "jsonrpc": "2.0",
  "id": "1",
  "error": {
    "name": "SocialAuthError",
    "message": "No record found for this Facebook account",
    "code": 1000
  }
}
```

```json-doc
{
  "name": "SocialAuthError",
  "message": "No record found for this Facebook account",
  "code": 1000
}
```

> The following is the result of a bad access token where either the token does not belong to the application or the token has expired

```json
{
  "jsonrpc": "2.0",
  "id": "1",
  "error": {
    "name": "SocialAuthError",
    "message": "Failed to fetch user profile",
    "code": 1009
  }
}
```

```json-doc
{
  "name": "SocialAuthError",
  "message": "Failed to fetch user profile",
  "code": 1009
}
```

This endpoint accepts a single argument `access_token` the was given by the Facebook SDK and will validate the access_token. If the API is able to find a profile using this access token, the API will attempt to find a user account that exists with the given `facebookId` from the profile. Providing one exists, the user object will be returned in the `result` field of the Response Body. If there was a problem, the description will be provided in the `error` field of the response body.

### RPC Method Name
`users.loginFB`


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Pickup Dropped Item

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "method": "users.pickupItem",
  "id": "1234",
  "params": {
    "userId": "unique-user-id",
    "itemId": "unique-item-id"
  }
}
```

```json-doc

```

> The above command returns JSON structured like this:

```json
{
  "jsonrpc": "2.0",
  "id": "",
  "result": {
    "createdAt": "2016-11-11T19:52:08.000Z",
    "email": "testing@test.com",
    "fbId": "98723874623",
    "id": "6abd8d81-c24d-41a6-bee7-db49efd2c70d",
    "username": "testingUser",
    "gender": 0,
    "age": 28,
    "city": "Huntington Beach",
    "location": {
      "latitude": 0,
      "longitude": 0
    },
    "inventory": {
      "baseInvCount": 75,
      "createdAt": "2016-12-10T03:37:36.566Z",
      "id": "c6aad8c0-fac2-4112-9f39-24861c7f5a9d",
      "items": [
        {
          "active": true,
          "createdAt": "2016-12-14T22:01:59.950Z",
          "id": "1ce2ede0-57c1-46ad-8a15-dc1c9d9e3293",
          "invId": "c6aad8c0-fac2-4112-9f39-24861c7f5a9d",
          "item": {
            "animType": 0,
            "createdAt": "2016-12-10T03:37:36.574Z",
            "damage": "M",
            "description": "UH! apple-pen",
            "id": "9a3cd94d-79d2-4378-a011-fb68c139191b",
            "name": "Apple-Pen",
            "rarity": 3,
            "type": 0
          },
          "itemId": "9a3cd94d-79d2-4378-a011-fb68c139191b"
        }
      ],
      "level": 1,
      "userId": "d3b0a471-eb99-42a6-9d87-76299abfd64a"
    }
  }
}
```

```json-doc

```

This method is used for a user to pickup a dropped item on the map and add it to their inventory

### RPC Method Name
`users.pickupItem`

### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.pickupItem` |
| params | Object | Contains fields needed to perform the action |
| params.userId | String | Unique user id attempting to pickup an item |
| params.itemId | String | Unique id of the item the user is attempting to pickup |

### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | Contains the [UserModel](#user) that has the full [Inventory](#inventory) details, including [Item](#item) details |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Discard Inventory Items

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "method": "users.trashItems",
  "id": "1234",
  "params": {
    "userId": "unique-user-id",
    "itemId": "unique-item-id",
    "quantity": 1
  }
}
```

```json-doc

```

> The above command returns JSON structured like this:

```json
{
  "jsonrpc": "2.0",
  "id": "",
  "result": {
    "createdAt": "2016-11-11T19:52:08.000Z",
    "email": "testing@test.com",
    "fbId": "98723874623",
    "id": "6abd8d81-c24d-41a6-bee7-db49efd2c70d",
    "username": "testingUser",
    "gender": 0,
    "age": 28,
    "city": "Huntington Beach",
    "location": {
      "latitude": 0,
      "longitude": 0
    },
    "inventory": {
      "baseInvCount": 75,
      "createdAt": "2016-12-10T03:37:36.566Z",
      "id": "c6aad8c0-fac2-4112-9f39-24861c7f5a9d",
      "items": [
        {
          "active": true,
          "createdAt": "2016-12-14T22:01:59.950Z",
          "id": "1ce2ede0-57c1-46ad-8a15-dc1c9d9e3293",
          "invId": "c6aad8c0-fac2-4112-9f39-24861c7f5a9d",
          "item": {
            "animType": 0,
            "createdAt": "2016-12-10T03:37:36.574Z",
            "damage": "M",
            "description": "UH! apple-pen",
            "id": "9a3cd94d-79d2-4378-a011-fb68c139191b",
            "name": "Apple-Pen",
            "rarity": 3,
            "type": 0
          },
          "itemId": "9a3cd94d-79d2-4378-a011-fb68c139191b"
        }
      ],
      "level": 1,
      "userId": "d3b0a471-eb99-42a6-9d87-76299abfd64a"
    }
  }
}
```

```json-doc

```

### RPC Method Name
`users.trashItems`

### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.trashItems` |
| params | Object | Contains fields needed to perform the action |
| params.userId | String | Unique user id attempting to discard an item |
| params.itemId | String | Unique item id of the item the user wants to get rid of |
| params.quantity | Number | A number value representing how many of the specified item the user would like to part with. ___If not provided, currently the API will default to 1___ |

### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | Contains the [UserModel](#user) that has the full [Inventory](#inventory) details, including [Item](#item) details. This is the new representation of the user's inventory, minus the item/s that was just removed |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Get User's Inventory

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "method": "users.getUserInventory",
  "id": "1234",
  "params": {
    "userId": "unique-user-id"
  }
}
```

```json-doc

```

> The above command returns JSON structured like this:

```json
{
  "jsonrpc": "2.0",
  "id": "",
  "result": {
    "createdAt": "2016-11-11T19:52:08.000Z",
    "email": "testing@test.com",
    "fbId": "98723874623",
    "id": "6abd8d81-c24d-41a6-bee7-db49efd2c70d",
    "username": "testingUser",
    "gender": 0,
    "age": 28,
    "city": "Huntington Beach",
    "location": {
      "latitude": 0,
      "longitude": 0
    },
    "inventory": {
      "baseInvCount": 75,
      "createdAt": "2016-12-10T03:37:36.566Z",
      "id": "c6aad8c0-fac2-4112-9f39-24861c7f5a9d",
      "items": [
        {
          "active": true,
          "createdAt": "2016-12-14T22:01:59.950Z",
          "id": "1ce2ede0-57c1-46ad-8a15-dc1c9d9e3293",
          "invId": "c6aad8c0-fac2-4112-9f39-24861c7f5a9d",
          "item": {
            "animType": 0,
            "createdAt": "2016-12-10T03:37:36.574Z",
            "damage": "M",
            "description": "UH! apple-pen",
            "id": "9a3cd94d-79d2-4378-a011-fb68c139191b",
            "name": "Apple-Pen",
            "rarity": 3,
            "type": 0
          },
          "itemId": "9a3cd94d-79d2-4378-a011-fb68c139191b"
        }
      ],
      "level": 1,
      "userId": "d3b0a471-eb99-42a6-9d87-76299abfd64a"
    }
  }
}
```

```json-doc

```

This method is used for a user to pickup a dropped item on the map and add it to their inventory

### RPC Method Name
`users.getUserInventory`

### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.getUserInventory` |
| params | Object | Contains fields needed to perform the action |
| params.userId | String | Unique user id attempting to pickup an item |

### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | Contains the [UserModel](#user) that has the full [Inventory](#inventory) details, including [Item](#item) details |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Spawn Dropped Items for User

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "method": "users.spawnItems",
  "id": "1234",
  "params": {
    "userId": "unique-user-id"
  }
}
```

```json-doc

```

> The above command returns JSON structured like this:

```json
{
  "jsonrpc": "2.0",
  "id": "1",
  "result": [
    {
      "createdAt": "2016-12-15T21:23:46.804Z",
      "id": "fee38167-eaae-4661-aad2-5eeb80137f18",
      "item": {
        "animType": 0,
        "createdAt": "2016-12-10T03:37:36.574Z",
        "damage": "XS",
        "description": "I hab a peeen",
        "id": "b03e33cd-9441-4cfe-9f90-631fd650fffd",
        "name": "Pen",
        "rarity": 1,
        "type": 0
      },
      "itemId": "b03e33cd-9441-4cfe-9f90-631fd650fffd",
      "userId": "d3b0a471-eb99-42a6-9d87-76299abfd64a"
    }
  ]
}
```

```json-doc

```

### RPC Method Name
`users.spawnItems`

### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.spawnItems` |
| params | Object | Contains fields needed to perform the action |
| params.userId | String | Unique user id attempting to pickup an item |

### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Array | An list of [InventoryItems](#inventoryitem) with the joined [Item](#item) details in the `item` field |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Engage A User

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "method": "engagements.engageUser",
  "id": "1234",
  "params": {
    "fromUId": "f33ceb35-9847-4d1d-a3d2-dd1649661657",
    "toUId": "d3b0a471-eb99-42a6-9d87-76299abfd64a"
  }
}
```

```json-doc

```

> The above command returns JSON structured like this:

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "result": {
    "fromUId": "f33ceb35-9847-4d1d-a3d2-dd1649661657",
    "toUId": "d3b0a471-eb99-42a6-9d87-76299abfd64a",
    "createdAt": "2017-01-25T01:51:02.600Z",
    "status": 0,
    "hits": 0,
    "misses": 0,
    "id": "4929a07f-37e0-4d93-8772-4b4738b5b98b"
  }
}
```

```json-doc

```

### RPC Method Name
`engagements.engageUser`

### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `engagements.engageUser` |
| params | Object | Contains fields needed to perform the action |
| params.fromUId | String | The unique userId who is initiating the Engagement (Battle) |
| params.toUId | String | The unique userId who the current user is choosing to Engage |

### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | An [Engagement](#engagement) with the initialized fields |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Update Engagement With User

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "method": "engagements.updateEngagement",
  "id": "1234",
  "params": {
    "engagementId": "781b62f6-860d-4f60-9fe7-c9e7e7881d7a",
    "isHit": 1,
    "userId": "f33ceb35-9847-4d1d-a3d2-dd1649661657",
    "itemId": "b03e33cd-9441-4cfe-9f90-631fd650fffd"
  }
}
```

```json-doc

```

> The above command returns JSON structured like this:

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "result": {
    "createdAt": "2017-01-25T03:00:37.412Z",
    "fromUId": "f33ceb35-9847-4d1d-a3d2-dd1649661657",
    "from_user": {
      "cirty": "Huntington Beach",
      "createdAt": "2017-01-11T23:48:18.237Z",
      "email": "zerosk8er194@gmail.com",
      "fbId": "10208099895402377",
      "gender": 0,
      "id": "f33ceb35-9847-4d1d-a3d2-dd1649661657",
      "inventory": {
        "baseInvCount": 75,
        "createdAt": "2017-01-11T23:48:18.273Z",
        "id": "1bc97fdc-69ee-4aaa-844e-d0cb5c0694aa",
        "items": [
          {
            "active": true,
            "createdAt": "2017-01-24T01:47:39.025Z",
            "id": "89341498-28e9-4f82-8dc6-2dcb13e691c0",
            "invId": "1bc97fdc-69ee-4aaa-844e-d0cb5c0694aa",
            "item": {
              "animType": 0,
              "createdAt": "2016-12-10T03:37:36.574Z",
              "damage": "XS",
              "description": "I hab a peeen",
              "id": "b03e33cd-9441-4cfe-9f90-631fd650fffd",
              "name": "Pen",
              "rarity": 1,
              "type": 0
            },
            "itemId": "b03e33cd-9441-4cfe-9f90-631fd650fffd"
          },
          {
            "active": true,
            "createdAt": "2017-01-24T01:48:27.532Z",
            "id": "5027a086-5ceb-4117-867b-2e5ff68eafc3",
            "invId": "1bc97fdc-69ee-4aaa-844e-d0cb5c0694aa",
            "item": {
              "animType": 0,
              "createdAt": "2016-12-10T03:37:36.574Z",
              "damage": "S",
              "description": "I hab pineappoo",
              "id": "f0ed5a51-4a2f-40d8-a931-b6907e52a3f4",
              "name": "Pineapple",
              "rarity": 2,
              "type": 0
            },
            "itemId": "f0ed5a51-4a2f-40d8-a931-b6907e52a3f4"
          },
          {
            "active": true,
            "createdAt": "2017-01-24T01:47:40.471Z",
            "id": "106b1c61-06fc-4f3c-8de6-0913a28e6b45",
            "invId": "1bc97fdc-69ee-4aaa-844e-d0cb5c0694aa",
            "item": {
              "animType": 0,
              "createdAt": "2016-12-10T03:37:36.574Z",
              "damage": "XS",
              "description": "I hab a peeen",
              "id": "b03e33cd-9441-4cfe-9f90-631fd650fffd",
              "name": "Pen",
              "rarity": 1,
              "type": 0
            },
            "itemId": "b03e33cd-9441-4cfe-9f90-631fd650fffd"
          },
          {
            "active": true,
            "createdAt": "2017-01-24T01:47:38.018Z",
            "id": "5a002bd2-02e0-4cb4-8ba5-b9c8f3cb41b5",
            "invId": "1bc97fdc-69ee-4aaa-844e-d0cb5c0694aa",
            "item": {
              "animType": 0,
              "createdAt": "2016-12-10T03:37:36.574Z",
              "damage": "XS",
              "description": "I hab a peeen",
              "id": "b03e33cd-9441-4cfe-9f90-631fd650fffd",
              "name": "Pen",
              "rarity": 1,
              "type": 0
            },
            "itemId": "b03e33cd-9441-4cfe-9f90-631fd650fffd"
          },
          {
            "active": true,
            "createdAt": "2017-01-24T01:48:01.963Z",
            "id": "d38cd87e-351f-4434-809e-2bd4a8bbe62b",
            "invId": "1bc97fdc-69ee-4aaa-844e-d0cb5c0694aa",
            "item": {
              "animType": 0,
              "createdAt": "2016-12-10T03:37:36.574Z",
              "damage": "XS",
              "description": "I hab a peeen",
              "id": "b03e33cd-9441-4cfe-9f90-631fd650fffd",
              "name": "Pen",
              "rarity": 1,
              "type": 0
            },
            "itemId": "b03e33cd-9441-4cfe-9f90-631fd650fffd"
          }
        ],
        "level": 1,
        "userId": "f33ceb35-9847-4d1d-a3d2-dd1649661657"
      },
      "username": "shaggydev"
    },
    "hits": 1,
    "id": "781b62f6-860d-4f60-9fe7-c9e7e7881d7a",
    "misses": 0,
    "status": 0,
    "toUId": "d3b0a471-eb99-42a6-9d87-76299abfd64a",
    "updatedAt": "2017-01-25T03:00:51.305Z"
  }
}
```

```json-doc

```

### RPC Method Name
`engagements.updateEngagement`

### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `engagements.updateEngagement` |
| params | Object | Contains fields needed to perform the action |
| params.engagementId | String | The unique Engagment Id usually retrieved after calling [Engage User](#engage-a-user)|
| params.isHit | Boolean | A number value representing if the throw was a hit or a miss. Only values allowed are `true` and `false` where `true = Hit` and `false = Miss`.  |
| params.userId | String | The unique userId of the current user who is fighting |
| params.itemId | String | The unique itemId of the [Item](#item) object to record what items are being used in the engagement and to make sure to remove an instance of this item from the user's inventory. |

### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | An [Engagement](#engagement) with the updated engagement information. The `fromUser` field will be included containing the user object with the updated inventory and intentory item details.  |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Finish Engagement

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "method": "engagements.finishEngagement",
  "id": "1234",
  "params": {
    "engagementId": "781b62f6-860d-4f60-9fe7-c9e7e7881d7a",
    "win": true
  }
}
```

```json-doc

```

> The above command returns JSON structured like this:

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "result": {
    "items": [
      {
        "createdAt": "2017-01-25T06:05:24.671Z",
        "id": "93eded1e-a833-49c3-a387-c4d88ee2b746",
        "item": {
          "animType": 0,
          "createdAt": "2016-12-10T03:37:36.574Z",
          "damage": "S",
          "description": "I hab a appoo",
          "id": "decabf42-67b2-45ca-87dc-ee48f8c98116",
          "name": "Apple",
          "rarity": 2,
          "type": 0
        },
        "itemId": "decabf42-67b2-45ca-87dc-ee48f8c98116",
        "userId": "d3b0a471-eb99-42a6-9d87-76299abfd64a"
      },
      {
        "createdAt": "2017-01-25T06:05:24.686Z",
        "id": "7324061e-6543-4ec6-bff3-b1a714563257",
        "item": {
          "animType": 0,
          "createdAt": "2016-12-10T03:37:36.574Z",
          "damage": "XS",
          "description": "I hab a peeen",
          "id": "b03e33cd-9441-4cfe-9f90-631fd650fffd",
          "name": "Pen",
          "rarity": 1,
          "type": 0
        },
        "itemId": "b03e33cd-9441-4cfe-9f90-631fd650fffd",
        "userId": "d3b0a471-eb99-42a6-9d87-76299abfd64a"
      },
      {
        "createdAt": "2017-01-25T06:05:24.686Z",
        "id": "70a69caf-dbd0-42bb-afda-2a398c7ab976",
        "item": {
          "animType": 0,
          "createdAt": "2016-12-10T03:37:36.574Z",
          "damage": "M",
          "description": "UH! pineapple-pen",
          "id": "6ab0d79d-b248-4ceb-95b9-958aec277a36",
          "name": "Pineapple-Pen",
          "rarity": 3,
          "type": 0
        },
        "itemId": "6ab0d79d-b248-4ceb-95b9-958aec277a36",
        "userId": "d3b0a471-eb99-42a6-9d87-76299abfd64a"
      }
    ],
    "relationship": {
      "channelName": "f33ceb35-9847-4d1d-a3d2-dd1649661657_d3b0a471-eb99-42a6-9d87-76299abfd64a",
      "createdAt": "2017-01-25T03:57:14.925Z",
      "id": "f9724d2a-6d95-48db-b916-17033010b29b",
      "lastInitiator": "f33ceb35-9847-4d1d-a3d2-dd1649661657",
      "level": 0,
      "points": 1,
      "updatedAt": "2017-01-25T03:57:14.925Z",
      "userIds": [
        "f33ceb35-9847-4d1d-a3d2-dd1649661657",
        "d3b0a471-eb99-42a6-9d87-76299abfd64a"
      ]
    }
  }
}
```

```json-doc

```

### RPC Method Name
`engagements.finishEngagement`

### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `engagements.finishEngagement` |
| params | Object | Contains fields needed to perform the action |
| params.engagementId | String | The unique Engagment Id |
| params.win | Boolean | True if the engagement was a success; false if it was otherwise not a success |

### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The seerver will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | The is a custom response that will contain two keys: one to represent the list of reward items as `items` that can be picked up using the [PickupItem](#pickup-dropped-item) endpoint, and the other being the [Relationship](#relationship) stored in the field `relationship` |
| result.items | Array | An array of [Items](#item) that represent a user's "rewards" for engaging with another user. |
| result.relationship | Object | A [Relationship](#relationship) with the updated relatonship information. |
