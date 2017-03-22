# API Reference RPC

All endpoints will resolve with the following host (domain) name/address:

`http://localhost:3000`


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Users

[//]: # (==================================================================================================)
### Get All Users

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

#### RPC Method Name
`users.fetchUsers`

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Array | The result of the request. [userModel](#user) |


[//]: # (==================================================================================================)
### Get a Specific User

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

#### RPC Method Name
`users.fetchUser`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.fetchUser` |
| params | Object | A JSON object that contains the field `userId` with the string value of the unique user id. Example: ```{ "userId": "unique-user-id" }``` |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | The result of the request. [userModel](#user) |


[//]: # (==================================================================================================)
### Fetch A User Profile

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "users.fetchUserProfile",
  "params": {
    "userId": "fe883474-f89c-4d60-9017-4f5a7d3bbef2",
    "callerId": "cc65d388-b816-4d4c-8a79-a9d13c0868a3"
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
    "createdAt": "2017-02-13T23:52:40.757Z",
    "email": "testing001@test.com",
    "extendedProfile": {
      "createdAt": "2017-02-13T23:52:40.799Z",
      "id": "c1d01481-920b-444b-a733-21ee6fa2af69",
      "profileImages": [
        {
          "createdAt": "2017-02-14T00:13:50.267Z",
          "extendedProfileId": "c1d01481-920b-444b-a733-21ee6fa2af69",
          "fileExt": ".jpeg",
          "filename": "interesting",
          "id": "c6bf71e9-79e1-4b21-841b-d21c5b878e97",
          "isProfile": true,
          "order": 0,
          "updatedAt": "2017-02-14T18:45:44.530Z",
          "userId": "fe883474-f89c-4d60-9017-4f5a7d3bbef2",
          "imageUrl": "https://s3.amazonaws.com/gotchuu/dev/users/profileImages/fe883474-f89c-4d60-9017-4f5a7d3bbef2/c6bf71e9-79e1-4b21-841b-d21c5b878e97.jpeg"
        }
      ],
      "userId": "fe883474-f89c-4d60-9017-4f5a7d3bbef2"
    },
    "fbId": "908789324",
    "id": "fe883474-f89c-4d60-9017-4f5a7d3bbef2",
    "username": "testing001"
  }
}
```

```json-doc

```

This method takes in two argmuents `userId` and `calledId`, which are both userIds, and will return a [User](#user) object with the attached [ExtendedProfile](#extendedprofile) information included. The `callerId` will be used with the `userId` to determine the relationship between these two user's to see how much information should be returned of the user by `userId` to the caller by `callerId`. This method supports and expects that a user will be requesting for their own profile, so if `userId` and `callerId` are the same, the check against the relationship will be skipped and will return everything about the user being requested. 

#### RPC Method Name
`users.fetchUserProfile`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.fetchUserProfile` |
| params | Object | A JSON object that contains the field `userId` with the string value of the unique user id and the field `callerId` with the string value of the userId of the user requesting the other user's information. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | The result of the request. [userModel](#user) with [ExtendedProfile](#extendedprofile) attached |


[//]: # (==================================================================================================)
### Update User Profile

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "users.updateProfile",
  "params": {
    "data": {
      "userId": "d3b0a471-eb99-42a6-9d87-76299abfd64a",
      "city": "Irvine",
      "age": 20,
      "gender": 0,
      "inches": 70,
      "bio": "This is a stupid ass bio"
    }
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
    "createdAt": "2016-08-01T20:59:37.000Z",
    "email": "integrationtesting@gmail.com",
    "extendedProfile": {
      "age": 20,
      "bio": "This is a stupid bio",
      "city": "Irvine",
      "createdAt": "2017-02-14T08:51:37.278Z",
      "id": "653fecdc-b858-45cb-9e57-a02eaafdf4a9",
      "inches": 70,
      "profileImages": [
        {
          "createdAt": "2017-02-14T08:51:37.437Z",
          "extendedProfileId": "653fecdc-b858-45cb-9e57-a02eaafdf4a9",
          "fileExt": ".jpeg",
          "filename": "interesting",
          "id": "17da7c59-0aa6-43e2-a2d4-67a6dad11d73",
          "isProfile": false,
          "order": 0,
          "userId": "d3b0a471-eb99-42a6-9d87-76299abfd64a"
        }
      ],
      "userId": "d3b0a471-eb99-42a6-9d87-76299abfd64a"
    },
    "fbId": "9000",
    "id": "d3b0a471-eb99-42a6-9d87-76299abfd64a",
    "location": {
      "latitude": 33.650928,
      "longitude": -117.714303
    },
    "username": "JumpNShoot"
  }
}
```

```json-doc

```

This method is used to update a user's profile information. The only fields that will be updated are those that are specified in the request. The request takes in a single argument called `data` that could contain the several different fields to update. The `userId` field is the only **Required** field and if not included will throw an error in the body of the response. The method will return the full user profile including `profileImages` and should contain the changes added in the request.

#### RPC Method Name
`users.updateProfile`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.updateProfile` |
| params | Object | A JSON object that contains the field `data` where `data` is an Object where the keys passed will be directly related to the fields in the [ExtendedProfile](#extendedprofile) object to update and the values of these keys will be the new value to update the profile with. `data.userId` is the only required field in this request. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | The result of the request. [userModel](#user) with [ExtendedProfile](#extendedprofile) attached |


[//]: # (==================================================================================================)
### Register/Create new User

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "method": "users.registerUser",
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

<aside class="warning">
This method is now deprecated in favor for separate functions to register a user based on the type of authentication they choose.
See <a href="#register-with-facebook">Register With Facebook</a> and <a href="#register-with-email">Register With Email methods</a>.
</aside>
This method is used to create a new user account.

#### RPC Method Name
`users.registerUser`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.registerUser` |
| params | Object | Object that contains the field `userData` where the value is a JSON object that contains the userModel fields to save in the database |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | The result of the request. [userModel](#user) |


[//]: # (==================================================================================================)
### Register With Facebook

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "method": "users.registerUserWithFB",
  "id": "1234",
  "params": {
    "userData": {
      "fbId": "98723874623",
      "username": "testingUser",
      "extendedProfile": {
        "birthdate": "1988-01-14T00:00:00.000Z",
        "gender": 0,
        "city": "Huntington Beach",
        "inches": 70
      }
    }
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
    "fbId": "98723874623",
    "id": "6abd8d81-c24d-41a6-bee7-db49efd2c70d",
    "username": "testingUser"
  }
}
```

```json-doc
```

<aside class="notice">
Replacement for <a href="#register-create-new-user">Register/Create User new User</a>.
</aside>
This method is to be specifically used to signup a user where the preferred method of login would be through facebook login.

#### RPC Method Name
`users.registerUserWithFB`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.registerUserWithFB` |
| params | Object | Object that contains the field `userData` where the value is a JSON object that contains the userModel fields to save in the database |
| params.userData.fbId | String | **Reuqired** This is the facebook Id of the user's facebook account after authenticating through facebook. Used to verify login |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | The result of the request. [userModel](#user) |


[//]: # (==================================================================================================)
### Register With Email

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "method": "users.registerUser",
  "id": "1234",
  "params": {
    "userData": {
      "email": "someemail@email.com",
      "username": "testingUser",
      "password": "somePassword",
      "extendedProfile": {
        "birthdate": "1988-01-14T00:00:00.000Z",
        "gender": 0,
        "city": "Huntington Beach",
        "inches": 70
      }
    }
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
    "city": "Huntington Beach"
  }
}
```

```json-doc
```

<aside class="notice">
Replacement for <a href="#register-create-new-user">Register/Create User new User</a>.
</aside>
This method is specifically used for creating a new user account using the preference for a Manual login flow (passing email and password to login).

#### RPC Method Name
`users.registerUserWithEmail`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.registerUserWithEmail` |
| params | Object | Object that contains the field `userData` where the value is a JSON object that contains the userModel fields to save in the database |
| params.userData.email | String | **Required** This is the email that the user will use to login with when registering via email |
| params.userData.password | String | **Required** This is the password the user is choosing as their login credentials |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | The result of the request. [userModel](#user) |


[//]: # (==================================================================================================)
### Update User Location

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

#### RPC Method Name
`users.updatePosition`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.updatePosition` |
| params | Object | Object that contains the fields `userId` and `location` |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | The result of the request. [userModel](#user) |


[//]: # (==================================================================================================)
### Search for targets around User

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
      "username": "blargasaurus",
      "profileImages": [{}]
    }
  ]
}
```

This method will serve two purposes; it will require a location object with the latitude and longitude and update the calling user's location, and after this is successful, the API will run a geospatial query using this new geopoint location and a set radius to find any users in the database within the area of the calling user. 

<aside class="notice">This method will omit returning the calling user's object</aside>

#### RPC Method Name
`users.searchTargets`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.searchTargets` |
| params | Object | Object that contains the fields `userId` and `location` |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Array | The result of the request. Array of [userModels](#user). Within each of the user objects, a field `profileImages` will exist which will contain a single [FileUpload](#file-upload) object which should be the main profile image information. |


[//]: # (==================================================================================================)
### Login using Facebook

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
    "createdAt": "2016-11-11T19:52:08.000Z",
    "email": "thingy1@gmail.com",
    "fbId": "10207332672302279",
    "id": "another-unique-user-id",
    "location": {
      "latitude": 0,
      "longitude": 0
    },
    "username": "blargasaurus",
    "inventory": {},
    "extendedProfile": {}
  }
}
```

```json-doc
{
  "success": true,
  "result": {
    "createdAt": "2016-11-11T19:52:08.000Z",
    "email": "thingy1@gmail.com",
    "fbId": "10207332672302279",
    "id": "another-unique-user-id",
    "location": {
      "latitude": 0,
      "longitude": 0
    },
    "username": "blargasaurus",
    "inventory": {},
    "extendedProfile": {}
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

#### RPC Method Name
`users.loginFB`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.loginFB` |
| params | Object | Contains fields needed to perform the action |
| params.body.access_token | String | Facebook access token from client login to find user account with |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | Contains the [UserModel](#user) that has the full [Inventory](#inventory) details, including [Item](#item) details. Also includes the complete [ExtendedProfile](#extended-profile) for a found user with facebook login. |


[//]: # (==================================================================================================)
### Login using Manual Credentials

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "users.login",
  "params": {
    "body": {
      "username": "something@another.com",
      "password": "test123"
    }
  }
}
```

```json-doc
```

> The following is a successful login

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "result": {
    "createdAt": "2017-03-10T02:42:47.177Z",
    "email": "something@another.com",
    "extendedProfile": {
      "createdAt": "2017-03-10T02:42:47.284Z",
      "id": "125e85a8-dd84-4bb9-a563-93552115330c",
      "profileImages": [],
      "userId": "a4b4799d-55ef-41de-aa62-ef47a6d5b3da"
    },
    "id": "a4b4799d-55ef-41de-aa62-ef47a6d5b3da",
    "inventory": {
      "baseInvCount": 75,
      "createdAt": "2017-03-10T02:42:47.284Z",
      "id": "0a2d4942-ff4f-4b14-922f-545a3511e679",
      "items": [],
      "level": 1,
      "userId": "a4b4799d-55ef-41de-aa62-ef47a6d5b3da"
    },
    "username": "testing001"
  }
}
```

```json-doc
```

> The following result is when the email address provided in the "username" field of the request doesn't match an email address in the database

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "error": {
    "name": "SocialAuthError",
    "message": "No User Found by that email",
    "code": 1020
  }
}
```

```json-doc
```

> The following is when we have found a user account with the email provided in the "username" of the request but the password provided does not match

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "error": {
    "name": "SocialAuthError",
    "message": "Password was invalid for this user account",
    "code": 1022
  }
}
```

```json-doc
```

This method accepts a single parameter in the `params` property of the request called `body`. Inside `body`, two parameters should be passed that represent the user's crednetials: `username` which should be the email the user registered with, and `password` is the password given for the user account. Upon successful authentication, the full user profile will be returned with the complete inventory object and all of its item details.

#### RPC Method Name
`users.login`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| method | String | The name of the method to call on the server API. In this case: `users.login`. |
| params | Object | Contains fields needed to perform the action. |
| params.body.username | String | The email address that the user registed their account with. |
| params.body.password | String | The password that will be be used to check our records for a successful match. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | Contains the [UserModel](#user) that has the full [Inventory](#inventory) details, including [Item](#item) details. Also includes the complete [ExtendedProfile](#extended-profile) for a found user with facebook login. |


[//]: # (==================================================================================================)
### Pickup Dropped Item

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

#### RPC Method Name
`users.pickupItem`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.pickupItem` |
| params | Object | Contains fields needed to perform the action |
| params.userId | String | Unique user id attempting to pickup an item |
| params.itemId | String | Unique id of the item the user is attempting to pickup |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | Contains the [UserModel](#user) that has the full [Inventory](#inventory) details, including [Item](#item) details |


[//]: # (==================================================================================================)
### Discard Inventory Items

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

#### RPC Method Name
`users.trashItems`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.trashItems` |
| params | Object | Contains fields needed to perform the action |
| params.userId | String | Unique user id attempting to discard an item |
| params.itemId | String | Unique item id of the item the user wants to get rid of |
| params.quantity | Number | A number value representing how many of the specified item the user would like to part with. ___If not provided, currently the API will default to 1___ |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | Contains the [UserModel](#user) that has the full [Inventory](#inventory) details, including [Item](#item) details. This is the new representation of the user's inventory, minus the item/s that was just removed |


[//]: # (==================================================================================================)
### Get User's Inventory

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

#### RPC Method Name
`users.getUserInventory`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.getUserInventory` |
| params | Object | Contains fields needed to perform the action |
| params.userId | String | Unique user id attempting to pickup an item |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | Contains the [UserModel](#user) that has the full [Inventory](#inventory) details, including [Item](#item) details |


[//]: # (==================================================================================================)
### Spawn Dropped Items for User

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

#### RPC Method Name
`users.spawnItems`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.spawnItems` |
| params | Object | Contains fields needed to perform the action |
| params.userId | String | Unique user id attempting to pickup an item |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Array | An list of [InventoryItems](#inventoryitem) with the joined [Item](#item) details in the `item` field |


[//]: # (==================================================================================================)
### Replace Profile Image

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "method": "users.updateProfileImage",
  "id": "1234",
  "params": {
    "userId": "fe883474-f89c-4d60-9017-4f5a7d3bbef2",
    "fileId": "c6bf71e9-79e1-4b21-841b-d21c5b878e97"
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
    "createdAt": "2017-02-14T00:13:50.267Z",
    "extendedProfileId": "c1d01481-920b-444b-a733-21ee6fa2af69",
    "fileExt": ".jpeg",
    "filename": "interesting",
    "id": "c6bf71e9-79e1-4b21-841b-d21c5b878e97",
    "isProfile": true,
    "order": 0,
    "userId": "fe883474-f89c-4d60-9017-4f5a7d3bbef2"
  }
}
```

```json-doc

```

This method is used to change the user's main profile picture to another picture that they have already uploaded and exists in their list of profileImages in their [ExtendedProfile](#extendedprofile). This method will throw an error if the API finds that the fileId passed is not owned by the user with the userId specified in the request.

#### RPC Method Name
`users.updateProfileImage`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.updateProfileImage` |
| params | Object | Contains fields needed to perform the action |
| params.userId | String | The unique user Id whom wants to update their main profile image to a new one |
| params.fileId | String | The unique fileUploadId from the user's list of profileImages to promote to the main profile image. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | This method returns a [User](#user) model representing the full updated user profile which includes the full [ExtendedProfile](#extended-profile) with [FileUploads](#file-uploads) in the `profileImages` field of the `extendedProfile` |


[//]: # (==================================================================================================)
### Select User On Map

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "users.selectUserOnMap",
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
    "createdAt": "2016-08-01T20:59:37.000Z",
    "email": "integrationtesting@gmail.com",
    "extendedProfile": {
      "age": 20,
      "bio": "This is a stupid ass bio",
      "city": "Irvine",
      "createdAt": "2017-02-14T08:51:37.278Z",
      "id": "653fecdc-b858-45cb-9e57-a02eaafdf4a9",
      "inches": 70,
      "profileImages": [
        {
          "createdAt": "2017-02-14T08:51:37.437Z",
          "extendedProfileId": "653fecdc-b858-45cb-9e57-a02eaafdf4a9",
          "fileExt": ".jpeg",
          "filename": "interesting",
          "id": "17da7c59-0aa6-43e2-a2d4-67a6dad11d73",
          "isProfile": false,
          "order": 0,
          "userId": "d3b0a471-eb99-42a6-9d87-76299abfd64a",
          "imageUrl": "https://s3.amazonaws.com/gotchuu/dev/users/profileImages/d3b0a471-eb99-42a6-9d87-76299abfd64a/17da7c59-0aa6-43e2-a2d4-67a6dad11d73.jpeg"
        }
      ],
      "userId": "d3b0a471-eb99-42a6-9d87-76299abfd64a"
    },
    "fbId": "9000",
    "id": "d3b0a471-eb99-42a6-9d87-76299abfd64a",
    "location": {
      "latitude": 33.650928,
      "longitude": -117.714303
    },
    "username": "JumpNShootMan",
    "relationship": {
      "channelName": "f33ceb35-9847-4d1d-a3d2-dd1649661657_d3b0a471-eb99-42a6-9d87-76299abfd64a",
      "createdAt": "2017-01-25T03:57:14.925Z",
      "id": "f9724d2a-6d95-48db-b916-17033010b29b",
      "lastInitiator": "f33ceb35-9847-4d1d-a3d2-dd1649661657",
      "level": 3,
      "points": 7,
      "updatedAt": "2017-02-16T19:11:23.756Z",
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

The purpose of this method is to easily provide user profile information along side information about the potential relationship between the requesting user and the target user.

#### RPC Method Name
`users.selectUserOnMap`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `users.selectUserOnMap` |
| params | Object | Contains fields needed to perform the action |
| params.fromUId | String | The unique Id of the user who is requesting the information on a user from the map view. |
| params.toUId | String | The unique Id of the user who was found on the map and should be the subject of the response. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | The result of this function will be an object representing the [User](#user) which will contain the [ExtendedProfile](#extended-profile) information based on the level of the relationship. The user model will contain a custom key `realtionship` which will contain the relationship object between the two given users. |


[//]: # (==================================================================================================)
### Send Forgot Password Request
```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "users.forgotPassword",
  "params": {
    "email": "testing0003@test.com"
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
    "statusCode": 202,
    "body": "",
    "headers": {
      "server": "nginx",
      "date": "Thu, 16 Mar 2017 20:11:39 GMT",
      "content-type": "text/plain; charset=utf-8",
      "content-length": "0",
      "connection": "close",
      "x-message-id": "pcbA2aqTRI-OUyjDqm1Sxg",
      "x-frame-options": "DENY",
      "access-control-allow-origin": "https://sendgrid.api-docs.io",
      "access-control-allow-methods": "POST",
      "access-control-allow-headers": "Authorization, Content-Type, On-behalf-of, x-sg-elas-acl",
      "access-control-max-age": "600",
      "x-no-cors-reason": "https://sendgrid.com/docs/Classroom/Basics/API/cors.html"
    }
  }
}
```

> The following is the result if a user passes an email address that does not match an email record in our database

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "result": {
    "code": 1201,
    "message": "Email does not match any records in our database"
  }
}
```

```json-doc
```

This method is used to create a user request to reset their password. This method will attempt to find a user based on the email provided and if one is found, will use SendGrid to send an automated email with a link to reset their password. **However** it should be noted that if the user enters an email here that does not match one in our records, an error will be returned back.

#### RPC Method Name
`users.forgotPassword`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| method | String | The name of the method to call on the server API. In this case: `users.forgotPassword`. |
| params | Object | Contains fields needed to perform the action. |
| params.email | String | This is the email that is linked to the user that we want to reset the password for and send the email to for the reset password link. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| result | Object | This will be a response from sendgrid that the email was successful. This response can be ignored since it doesn't contain anything of direct use. |


[//]: # (==================================================================================================)
### Clear User's Badge Count
```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "users.clearUserBadge",
  "params": {
    "userId": "0706744d-d0bd-4f0b-a5e9-3f3c49aad20b"
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
    "badge": 0,
    "createdAt": "2017-03-21T01:27:43.904Z",
    "fbId": "00019283674",
    "ftueComplete": false,
    "id": "0706744d-d0bd-4f0b-a5e9-3f3c49aad20b",
    "username": "testing001"
  }
}
```

```json-doc
```

The purpose of this method is to control the user's app Icon badge count and clear it back to 0 when the user enters the app. This will aid in the methods that send out a push notification to increment a count that reflects a user's actions within the application. For example, If a user has recieved a couple push notifications, the user will see an app icon badge of '2'. The user then enters the application, the OS will clear the badge and the client app will call this method to clear the badge count back to 0. If user exists app again and recieves 3 more notifications, the app icon badge will reflect the proper count of '3' rather than '5' (then accumulation of all push notifications received in the user's short life time thus far).

#### RPC Method Name
`users.clearUserBadge`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| method | String | The name of the method to call on the server API. In this case: `users.clearUserBadge`. |
| params | Object | Contains fields needed to perform the action. |
| params.userId | String | The user id for the user we want to clear the badge count for. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| result | Object | The simple [User](#user) object with the updated badge count field (which sould be at 0). |


[//]: # (==================================================================================================)
### Mark Completed FTUE
```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "users.completedFTUE",
  "params": {
    "userId": "0706744d-d0bd-4f0b-a5e9-3f3c49aad20b"
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
    "badge": 0,
    "createdAt": "2017-03-21T01:27:43.904Z",
    "fbId": "00019283674",
    "ftueComplete": true,
    "id": "0706744d-d0bd-4f0b-a5e9-3f3c49aad20b",
    "username": "testing001"
  }
}
```

```json-doc
```

The purpose of this method is only to persist the event that a user has completed the FTUE (first time user experience). This aids the API in generating the [ActivityFeedItem](#activityfeeditem) for a user that has completed the FTUE.

#### RPC Method Name
`users.completedFTUE`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| method | String | The name of the method to call on the server API. In this case: `users.completedFTUE`. |
| params | Object | Contains fields needed to perform the action. |
| params.userId | String | The user id for the user we want to record that has completed the FTUE. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| result | Object | The simple [User](#user) object with the updated ftueCompleted field (which sould be true). |


[//]: # (==================================================================================================)
### Fetch Activity Feed
```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "users.fetchActivityFeed",
  "params": {
    "userId": "0706744d-d0bd-4f0b-a5e9-3f3c49aad20b",
    "lastActivityDate": "2017-03-21T01:27:43.904Z",
    "pageSize": 20
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
  "result": [
    {
      "actType": 3,
      "appId": "gotchuu",
      "createdAt": "2017-03-22T04:46:17.497Z",
      "id": "7e4201fa-b64f-410d-bf03-96632b68e000",
      "ownerId": "0706744d-d0bd-4f0b-a5e9-3f3c49aad20b",
      "seen": false,
      "owner": {
        "badge": 0,
        "createdAt": "2017-03-21T01:27:43.904Z",
        "extendedProfile": {
          "createdAt": "2017-03-21T01:27:43.924Z",
          "id": "069514da-ea9b-48a3-94c4-fba83cd750d8",
          "isComplete": false,
          "profileImages": [],
          "userId": "0706744d-d0bd-4f0b-a5e9-3f3c49aad20b"
        },
        "fbId": "00019283674",
        "ftueComplete": true,
        "id": "0706744d-d0bd-4f0b-a5e9-3f3c49aad20b",
        "inventory": {
          "baseInvCount": 75,
          "createdAt": "2017-03-21T01:27:43.924Z",
          "id": "e045be15-1651-4531-9e16-13e37fcd6bfe",
          "items": [],
          "level": 1,
          "userId": "0706744d-d0bd-4f0b-a5e9-3f3c49aad20b"
        },
        "username": "testing001"
      },
      "bodyText": "Tutorial completed!"
    }
  ]
}
```

```json-doc
```

The purpose of this method is to retrieve a list of [ActivityFeedItems](#activityfeeditem) for the given user. This is a paginiated response where the pageSize is defaulted to **20**. The paginiation style is setup for an infinite scroller where by providing the `lastActivityDate`, the API will return the next set of activity feed items starting from that timestamp with the amount specified by the `pageSize`. There are a couple different types of activity feed items so reference the [ActivityFeedItems](#activityfeeditem) model to get an idea of the potential fields that a response object can contain.

#### RPC Method Name
`users.fetchActivityFeed`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| method | String | The name of the method to call on the server API. In this case: `users.fetchActivityFeed`. |
| params | Object | Contains fields needed to perform the action. |
| params.userId | String | The user id for the user we want to record that has completed the FTUE. |
| params.lastActivityDate | String | **Optional** The date of the last activity you retrieved in ISO8601 format preferred. |
| params.pageSize | Number | **Optional** The total amount of objects you would like returned in the result. ***Default is 20*** |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| result | Array<[ActivityFeedItem](#activityfeeditem)> | An array of [ActivityFeedItems](#activityfeeditem). |


[//]: # (==================================================================================================)
### Mark Activity Feed Items as Read
```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "users.markActivityAsRead",
  "params": {
    "userId": "0706744d-d0bd-4f0b-a5e9-3f3c49aad20b"
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
    "updated": 2
  }
}
```

```json-doc
```

The purpose of this method is to mark all activity feed items as read once a user enters the [ActivityFeedItems](#activityfeeditem) list within the client application. This will aid the API in being able to provide the client app information about a user and if they have any "unseen" activity feed items so they can display some kind of indicator.

#### RPC Method Name
`users.markActivityAsRead`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| method | String | The name of the method to call on the server API. In this case: `users.markActivityAsRead`. |
| params | Object | Contains fields needed to perform the action. |
| params.userId | String | The user id for the user we want to mark their actiivty feed items as read for. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| result | Object | A simple result object with a single field `updated`. |
| result.updated | Number | A count of the amount of activity feed items that have been marked as "seen". |


[//]: # (==================================================================================================)
### Fetch Unseen Activity Feed Item Count
```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "users.fetchActivityUnreadCount",
  "params": {
    "userId": "0706744d-d0bd-4f0b-a5e9-3f3c49aad20b"
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
    "count": 2
  }
}
```

```json-doc
```

The purpose of this method is to simply retrieve the amount of activity feed items the given user has yet to "see".

#### RPC Method Name
`users.fetchActivityUnreadCount`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| method | String | The name of the method to call on the server API. In this case: `users.fetchActivityUnreadCount`. |
| params | Object | Contains fields needed to perform the action. |
| params.userId | String | The user id for the user we want to retrieve the amount of "unseen" activity feed items for. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| result | Object | A simple result object with a single field `count`. |
| result.count | Number | A count of the amount of activity feed items that have not been "seen" yet. |


[//]: # (==================================================================================================)

[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Engagements

[//]: # (==================================================================================================)
### Engage A User

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

#### RPC Method Name
`engagements.engageUser`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `engagements.engageUser` |
| params | Object | Contains fields needed to perform the action |
| params.fromUId | String | The unique userId who is initiating the Engagement (Battle) |
| params.toUId | String | The unique userId who the current user is choosing to Engage |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | An [Engagement](#engagement) with the initialized fields |


[//]: # (==================================================================================================)
### Update Engagement With User

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

#### RPC Method Name
`engagements.updateEngagement`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `engagements.updateEngagement` |
| params | Object | Contains fields needed to perform the action |
| params.engagementId | String | The unique Engagment Id usually retrieved after calling [Engage User](#engage-a-user)|
| params.isHit | Boolean | A number value representing if the throw was a hit or a miss. Only values allowed are `true` and `false` where `true = Hit` and `false = Miss`.  |
| params.userId | String | The unique userId of the current user who is fighting |
| params.itemId | String | The unique itemId of the [Item](#item) object to record what items are being used in the engagement and to make sure to remove an instance of this item from the user's inventory. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | An [Engagement](#engagement) with the updated engagement information. The `fromUser` field will be included containing the user object with the updated inventory and intentory item details.  |


[//]: # (==================================================================================================)
### Finish Engagement

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

#### RPC Method Name
`engagements.finishEngagement`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `engagements.finishEngagement` |
| params | Object | Contains fields needed to perform the action |
| params.engagementId | String | The unique Engagment Id |
| params.win | Boolean | True if the engagement was a success; false if it was otherwise not a success |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | The is a custom response that will contain two keys: one to represent the list of reward items as `items` that can be picked up using the [PickupItem](#pickup-dropped-item) endpoint, and the other being the [Relationship](#relationship) stored in the field `relationship` |
| result.items | Array | An array of [Items](#item) that represent a user's "rewards" for engaging with another user. |
| result.relationship | Object | A [Relationship](#relationship) with the updated relatonship information. |


[//]: # (==================================================================================================)

[//]: # (==================================================================================================)
[//]: # (==================================================================================================)


## Relationships

[//]: # (==================================================================================================)
### Fetch New Challenges For User

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "relationships.fetchNewConnections",
  "params": {
    "userId": "d3b0a471-eb99-42a6-9d87-76299abfd64a"
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
  "result": [
    {
      "channelName": "f33ceb35-9847-4d1d-a3d2-dd1649661657_d3b0a471-eb99-42a6-9d87-76299abfd64a",
      "createdAt": "2017-01-25T03:57:14.925Z",
      "id": "f9724d2a-6d95-48db-b916-17033010b29b",
      "lastInitiator": "f33ceb35-9847-4d1d-a3d2-dd1649661657",
      "level": 2,
      "points": 7,
      "updatedAt": "2017-03-08T19:56:27.369Z",
      "userIds": [
        "f33ceb35-9847-4d1d-a3d2-dd1649661657",
        "d3b0a471-eb99-42a6-9d87-76299abfd64a"
      ],
      "user": {
        "createdAt": "2017-01-11T23:48:18.237Z",
        "email": "zerosk8er194@gmail.com",
        "fbId": "10208099895402377",
        "id": "f33ceb35-9847-4d1d-a3d2-dd1649661657",
        "extendedProfile": {
          "id": "b43de21f-b598-4fe1-8e78-4e626ef6afd0",
          "age": 25,
          "profileImages": [
            {
              "createdAt": "2017-02-23T01:15:40.857Z",
              "extendedProfileId": "b43de21f-b598-4fe1-8e78-4e626ef6afd0",
              "fileExt": ".jpeg",
              "filename": "interesting",
              "id": "db126b3c-0919-417c-aa97-6ead4a6c6a02",
              "isProfile": true,
              "order": 0,
              "userId": "f33ceb35-9847-4d1d-a3d2-dd1649661657",
              "imageUrl": "https://s3.amazonaws.com/gotchuu/dev/users/profileImages/f33ceb35-9847-4d1d-a3d2-dd1649661657/db126b3c-0919-417c-aa97-6ead4a6c6a02.jpeg"
            }
          ],
          "userId": "f33ceb35-9847-4d1d-a3d2-dd1649661657"
        },
        "username": "shaggydev"
      }
    }
  ]
}
```

```json-doc

```

The purpose of this method is to retrieve a list of new connections for a given user. A new connection is defined as a relationship between two users where the `lastInitiator` field of the relationship object is NOT null AND is NOT the requesting user's Id. In short, a new connetions is defined as a fight that the other use has initiated towards the userId specified in the request. See [Relationship](#relationship) for field reference.

#### RPC Method Name
`relationships.fetchNewConnections`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| method | String | The name of the method to call on the server API. In this case: `relationships.fetchNewConnections`. |
| params | Object | Contains fields needed to perform the action. |
| params.userId | String | The unique Id of the user with which to retrieve the list of new connections for. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| result | Array | The result is an Array of [Relationship](#relationship) objects where the `lastInitiator` id is NOT the requesting userId (in other words, relationships where challenges are directed towards the userId specified in the request). Each realtionship object will have an added field `user` which will contain the "other" user's object with basic `extendedProfile` information. |


[//]: # (==================================================================================================)
### Ignore Challenge

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "relationships.ignoreChallenge",
  "params": {
    "relationshipId": "f9724d2a-6d95-48db-b916-17033010b29b",
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
    "channelName": "f33ceb35-9847-4d1d-a3d2-dd1649661657_d3b0a471-eb99-42a6-9d87-76299abfd64a",
    "createdAt": "2017-01-25T03:57:14.925Z",
    "id": "f9724d2a-6d95-48db-b916-17033010b29b",
    "lastInitiator": null,
    "level": 2,
    "points": 6,
    "updatedAt": "2017-02-16T19:11:23.756Z",
    "userIds": [
      "f33ceb35-9847-4d1d-a3d2-dd1649661657",
      "d3b0a471-eb99-42a6-9d87-76299abfd64a"
    ]
  }
}
```

```json-doc

```

The purpose of this method is to provide a way for a user to "ignore" a user's fight challenge and reset the state of the relationship back to a place where either user can now initiate the progression of the relationship.

#### RPC Method Name
`relationships.ignoreChallenge`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| method | String | The name of the method to call on the server API. In this case: `relationships.ignoreChallenge`. |
| params | Object | Contains fields needed to perform the action. |
| params.relationshipId | String | The unique Id of the relationship that the two users belong to and that the new challenge is associated with. |
| params.toUId | String | The unique Id of the user who has been challenged and is ellecting to "ignore" this challenge attempt. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| result | Object | The result of this method is an updated [Relationship](#relationship) object to signify that the "ignore" was successful. |


[//]: # (==================================================================================================)
### Fetch All Conversations/Relationships

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "relationships.fetchUserChatView",
  "params": {
    "userId": "d3b0a471-eb99-42a6-9d87-76299abfd64a"
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
  "result": [
    {
      "channelName": "f33ceb35-9847-4d1d-a3d2-dd1649661657_d3b0a471-eb99-42a6-9d87-76299abfd64a",
      "createdAt": "2017-01-25T03:58:10.056Z",
      "id": "e749e8ff-8260-484b-bef9-46a5fa3a4703",
      "level": 1,
      "points": 2,
      "lastInitiator": null,
      "userIds": [
        "f33ceb35-9847-4d1d-a3d2-dd1649661657",
        "d3b0a471-eb99-42a6-9d87-76299abfd64a"
      ],
      "user": {
        "createdAt": "2017-01-11T23:48:18.237Z",
        "email": "zerosk8er194@gmail.com",
        "fbId": "10208099895402377",
        "id": "f33ceb35-9847-4d1d-a3d2-dd1649661657",
        "profileImages": [],
        "username": "shaggydev"
      },
      "latestChat": [
        {
          "channelName": "f33ceb35-9847-4d1d-a3d2-dd1649661657_d3b0a471-eb99-42a6-9d87-76299abfd64a",
          "createdAt": "2017-02-25T08:33:48.387Z",
          "fromUId": "f33ceb35-9847-4d1d-a3d2-dd1649661657",
          "id": "32d3f620-0a4f-4fb2-ae3b-1475df1b05af",
          "message": "Back At you MAN!",
          "read": false,
          "timeStamp": "2017-02-25T08:33:48.365Z",
          "toUId": "d3b0a471-eb99-42a6-9d87-76299abfd64a"
        }
      ]
    }
  ]
}
```

```json-doc

```

The purpose of this method is to return a list of relationships that a user belongs to and provide all information to populate a Conversation View.

#### RPC Method Name
`relationships.fetchUserChatView`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `relationships.fetchUserChatView` |
| params | Object | Contains fields needed to perform the action |
| params.userId | String | The unique Id of the user who is requesting their list of conversations/relationships. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | The result of this function will be an Array of objects with each object representing the [Relationship](#relationship) model with a joined [User](#user) object and a joined [Chat](#chat) object array in the key `latestChat` at the root. Inside of the User modle will be an array of profileimages in the `profileImages` key which will be empty or contain one and only one object that has been labeled as the user's profile image with the imageUrl provided. This User model will represent the "Other" user in the relationship, the one that differs from the `userId` passed in to the request. |


[//]: # (==================================================================================================)

[//]: # (==================================================================================================)
[//]: # (==================================================================================================)


## ExtendedProfile


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)


## Chats

[//]: # (==================================================================================================)
### Send chat message

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "chats.sendMessage",
  "params": {
    "fromUId": "d3b0a471-eb99-42a6-9d87-76299abfd64a",
    "toUId": "f33ceb35-9847-4d1d-a3d2-dd1649661657",
    "message": "Hello World!",
    "relationshipId": "f9724d2a-6d95-48db-b916-17033010b29b"
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
    "fromUId": "d3b0a471-eb99-42a6-9d87-76299abfd64a",
    "channelName": "f33ceb35-9847-4d1d-a3d2-dd1649661657_d3b0a471-eb99-42a6-9d87-76299abfd64a",
    "toUId": "f33ceb35-9847-4d1d-a3d2-dd1649661657",
    "message": "Hello World!",
    "timeStamp": "2017-03-08T17:24:50.696Z",
    "createdAt": "2017-03-08T17:24:50.719Z",
    "read": false,
    "id": "95989bbd-251b-45b1-bec6-3043fa0a43f5"
  }
}
```

```json-doc

```

The purpose of this method is to facilitate the publishing of a message from one user to another based on their relationship and relationship level. If all validation checks out, a chat message will be saved to the database and the message will be published to our real-time service (PubNub) to power the real-time chat communication within the application.

#### RPC Method Name
`chats.sendMessage`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `chats.sendMessage` |
| params | Object | Contains fields needed to perform the action |
| params.fromUId | String | This is the unique user Id of the sender user. |
| params.toUId | String | This is the unique user Id of the receiver of the message. |
| params.message | String | The body/content of the message being sent. |
| params.relationshipId | String | The unique Id of the realtionship object retrieved earlier. We ask for this so we can do some verification/validation to ensure these two users really can chat where searching by the ID is much more reliable. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | The result is the object representation of the [Chat](#chat) message in the database |


[//]: # (==================================================================================================)
### Fetch Chat Message History

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "chats.fetchChatHistory",
  "params": {
    "userId": "d3b0a471-eb99-42a6-9d87-76299abfd64a",
    "relationshipId": "f9724d2a-6d95-48db-b916-17033010b29b"
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
    "user": {
      "createdAt": "2017-01-11T23:48:18.237Z",
      "email": "zerosk8er194@gmail.com",
      "fbId": "10208099895402377",
      "gender": 0,
      "id": "f33ceb35-9847-4d1d-a3d2-dd1649661657",
      "profileImages": [],
      "username": "shaggydev"
    },
    "messages": [
      {
        "channelName": "f33ceb35-9847-4d1d-a3d2-dd1649661657_d3b0a471-eb99-42a6-9d87-76299abfd64a",
        "createdAt": "2017-03-08T17:29:19.114Z",
        "fromUId": "d3b0a471-eb99-42a6-9d87-76299abfd64a",
        "id": "6e2b906c-303f-4aa0-ace5-6b1364b23ed9",
        "message": "World, Hello!",
        "read": false,
        "timeStamp": "2017-03-08T17:29:19.093Z",
        "toUId": "f33ceb35-9847-4d1d-a3d2-dd1649661657"
      }
    ]
}
```

```json-doc

```

The purpose of this method is to return a history of chat messages within a given relation/conversation that is ordered by most recent message on top (DESC order). 

#### RPC Method Name
`chats.fetchChatHistory`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `chats.fetchChatHistory` |
| params | Object | Contains fields needed to perform the action |
| params.userId | String | This is the unique user Id of the user requesting chat history. |
| params.relationshipId | String | The unique Id of the realtionship object retrieved earlier. |
| params.lastTimeStamp | String | **Optional** This is a field that will power the infinite scrolling paginiation of chat history. This field should be populated with the value of the `timeStamp` property of the last (oldest) chat message recieved. Using this field, the API will return the next set of 10 chat messages starting from the provided date. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Object | The result is going to be a custom response with just two keys; `user` and `messages` |
| result.user | Object | This object is going to be the [User](#user) model object of the "receiving" user, opposite of the user of the Id passed into the request. We have this on the top level of the response rather than within each chat message to reduce the repition of data within each chat message. |
| result.messages | Array | This is going to be an Array of [Chat](#chat) model objects ordered by most recent first (Desc). |


[//]: # (==================================================================================================)
### Mark Chat Messages as Read

```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "chats.markChatRead",
  "params": {
    "toUId": "d3b0a471-eb99-42a6-9d87-76299abfd64a",
    "relationshipId": "f9724d2a-6d95-48db-b916-17033010b29b"
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
  "result": [
    {
      "channelName": "f33ceb35-9847-4d1d-a3d2-dd1649661657_d3b0a471-eb99-42a6-9d87-76299abfd64a",
      "createdAt": "2017-03-08T17:24:50.719Z",
      "fromUId": "d3b0a471-eb99-42a6-9d87-76299abfd64a",
      "id": "95989bbd-251b-45b1-bec6-3043fa0a43f5",
      "message": "Hello World!",
      "read": true,
      "timeStamp": "2017-03-08T17:24:50.696Z",
      "toUId": "f33ceb35-9847-4d1d-a3d2-dd1649661657"
    }
  ]
}
```

```json-doc

```

This method is used to mark all messages that a user has recieved on a specific relationship/conversation as `read`.

#### RPC Method Name
`chats.markChatRead`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| method | String | The name of the method to call on the server API. In this case: `chats.markChatRead` |
| params | Object | Contains fields needed to perform the action |
| params.toUId | String | This is the unique user Id of the user requesting to read their unread messages. |
| params.relationshipId | String | The unique Id of the realtionship object that represents the conversation between the two users. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with |
| result | Array | The result of this method is an Array of [Chat](#chat) model objects of those that have been marked as `read` (with the field `read: true`). |


[//]: # (==================================================================================================)
### Fetch Unread Chat Message Count
```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "chats.fetchUnreadChatCount",
  "params": {
    "toUId": "f33ceb35-9847-4d1d-a3d2-dd1649661657",
    "channelName": "f33ceb35-9847-4d1d-a3d2-dd1649661657_d3b0a471-eb99-42a6-9d87-76299abfd64a"
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
    "count": 0
  }
}
```

```json-doc

```

This method's sole purpose is to return a number value that represents the unread message count for a recieving user in the provided channelName (Conversation).

#### RPC Method Name
`chats.fetchUnreadChatCount`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| method | String | The name of the method to call on the server API. In this case: `chats.fetchUnreadChatCount`. |
| params | Object | Contains fields needed to perform the action. |
| params.toUId | String | This is the unique user Id of the user requesting to read their unread messages. |
| params.channelName | String | This should be the full channel name that is provided through the relationship/conversation object in the `channelName` field. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| result | Object | The result is a simple object with a single key `count` that will contain a number value representing the unread message count for a user in a given channelName (Conversation). |


[//]: # (==================================================================================================)

[//]: # (==================================================================================================)
[//]: # (==================================================================================================)


## Blocks


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)



### Blocking a User
```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "blocks.blockUser",
  "params": {
    "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
    "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab"
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
    "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
    "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab",
    "createdAt": "2017-03-21T18:39:26.495Z",
    "id": "c3105b78-61e1-48a4-ba95-30eb8df7d514"
  }
}
```


This method is called upon to block couple of users in the system. FromUId is the user that initiates and blocks the toUId user. Here on, the world map and any other activities these two users will not be associated together. 

#### RPC Method Name
`blocks.blockUser`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| method | String | The name of the method to call on the server API. In this case: `blocks.blockUser`. |
| params | Object | Contains fields needed to perform the action. |
| params.fromUId | String | User initiating the block |
| params.toUId | String | User getting blocked to fromUId network. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| result | Object | The blocked object just inserted with users information |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)


### Checking if users are blocked to each other.
```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "blocks.areUsersBlocked",
  "params": {
    "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
    "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab"
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
  "result": true
}
```


This method is called to check if two users are blocked to each other. Returns a true or false boolean value.

#### RPC Method Name
`blocks.areUsersBlocked`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| method | String | The name of the method to call on the server API. In this case: `blocks.areUsersBlocked`. |
| params | Object | Contains fields needed to perform the action. |
| params.fromUId | String | User initiating the block |
| params.toUId | String | User getting blocked to fromUId network. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| result | Boolean | Boolean value if the users blocked model exist in the DB. |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)


### Get Block Between Users.
```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "blocks.getBlockBetweenUsers",
  "params": {
    "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
    "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab"
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
    "createdAt": "2017-03-21T17:47:59.551Z",
    "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
    "fromUser": {
      "createdAt": "2017-02-27T21:30:29.777Z",
      "email": "ankit@test.com",
      "fbId": "10211339070857649",
      "id": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
      "username": "ankibunkers",
      "ftueComplete": false,
      "badge": 0
    },
    "id": "c4d88db5-09f9-4970-977a-a417e0d9e369",
    "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab",
    "toUser": {
      "city": "irvine",
      "createdAt": "2017-01-03T23:10:03.004Z",
      "email": "ankit@uci.edu",
      "id": "81cd8e07-3031-42de-9f30-b71b40d7eaab",
      "username": "ankit",
      "ftueComplete": false,
      "badge": 0
    }
  }
}
```


This method is called to get blocked users joined with user info.

#### RPC Method Name
`blocks.getBlockBetweenUsers`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| method | String | The name of the method to call on the server API. In this case: `blocks.getBlockBetweenUsers`. |
| params | Object | Contains fields needed to perform the action. |
| params.fromUId | String | User initiating the block |
| params.toUId | String | User getting blocked to fromUId network. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| result | Object | Blocked object joined with both the user models. |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)



###  Get Users I am blocking.
```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "blocks.blockedUsersForMe",
  "params": {
    "userId": "45dcb0a4-38d2-4381-a4ea-f5d866445038"
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
  "result": [
    {
      "createdAt": "2017-03-21T17:47:59.551Z",
      "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
      "id": "c4d88db5-09f9-4970-977a-a417e0d9e369",
      "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab"
    },
    {
      "createdAt": "2017-03-21T17:47:03.462Z",
      "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
      "id": "e3fd48e9-c266-448b-ba8a-56a74cae0b80",
      "toUId": "82cd8e8a-5f4e-4d8f-96d8-973be966c4e2"
    }
  ]
}
```


This method is called to get all the users blocked by a single user by passing in the fromUId.

#### RPC Method Name
`blocks.blockedUsersForMe`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| method | String | The name of the method to call on the server API. In this case: `blocks.blockedUsersForMe`. |
| params | Object | Contains fields needed to perform the action. |
| params.userId | String | User initiating the block |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| result | Object | Array of blocked data models. |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)



###  Get all the users that has blocked a given user, passing in toUId.
```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "blocks.iAmBlockedBy",
  "params": {
    "userId": "81cd8e07-3031-42de-9f30-b71b40d7eaab"
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
  "result": [
     {
       "createdAt": "2017-03-21T17:47:59.551Z",
       "fromUId": "82cd8e8a-5f4e-4d8f-96d8-973be966c4e2",
       "id": "c4d88db5-09f9-4970-977a-a417e0d9e369",
       "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab"
     },
     {
       "createdAt": "2017-03-21T17:47:03.462Z",
       "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
       "id": "e3fd48e9-c266-448b-ba8a-56a74cae0b80",
       "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab"
     }
   ]
}
```

This method is called to get all the users that has blocked a given user, passing in toUId.

#### RPC Method Name
`blocks.iAmBlockedBy`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| method | String | The name of the method to call on the server API. In this case: `blocks.iAmBlockedBy`. |
| params | Object | Contains fields needed to perform the action. |
| params.userId | String | User Id of the user who has been blocked. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| result | Array | Array of blocked data models. |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)



###  Remove A Block
```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "blocks.removeUsersBlock",
  "params": {
    "blockId": "82cd8e8a-5f4e-4d8f-96d8-973be966c4e2",
    "callerId": "0706744d-d0bd-4f0b-a5e9-3f3c49aad20b"
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
  "result":  "block removed!"
}
```


This method is called to get all the users that has blocked a given user, passing in toUId.

#### RPC Method Name
`blocks.removeUsersBlock`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| method | String | The name of the method to call on the server API. In this case: `blocks.removeUsersBlock`. |
| params | Object | Contains fields needed to perform the action. |
| params.blockId | String | The id of the [Block](#block) object . |
| params.callerId | String | The id of the user (fromUId) that would like to lift the [Block](#block). |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| result | String | response that the object is removed from the db. |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)


## Report


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)



### Report a user
```json
"POST /rpc HTTP/1.1"
```

```json
{
  "jsonrpc": "2.0",
  "id": "1234",
  "method": "reports.reportUser",
  "params": {
    "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
    "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab",
    "reason": 1
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
    "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
    "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab",
    "createdAt": "2017-03-21T18:39:26.495Z",
    "id": "c3105b78-61e1-48a4-ba95-30eb8df7d514",
    "reason": 1,
    "status": 1
  }
}
```

This method is called upon by a user to report another user in the app for a particular reason. Pass in the integer value for reason why this user is being reported.

#### RPC Method Name
`reports.reportUser`

#### Request Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| method | String | The name of the method to call on the server API. In this case: `reports.reportUser`. |
| params | Object | Contains fields needed to perform the action. |
| params.fromUId | String | User reporting |
| params.toUId | String | User being reported. |
| params.reason | Integer | Specific value corresponding to a string reason. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| jsonrpc | String | Defines what version of the JSON-RPC the call is utilizing. |
| id | String | Used in the JSON-RPC 2.0 specificaion. The value tells the server that the client expects results back. The server will return data in the "result" field as well as pass the same "id" value back so the client knows what request the data returned is associated with. |
| result | Object | Contains the reported object just inserted in the db, contains an integer value of reason and a integer value indicating the status of this report. |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Notification


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)



### Notification Model and payload object information.
```json
"POST /rpc HTTP/1.1"
```

```json
{
  "userId": "81cd8e07-3031-42de-9f30-b71b40d7eaab",
  "channelKey": "gotchuu_push:81cd8e07-3031-42de-9f30-b71b40d7eaab"
}
```

```json-doc

```

> The notification object looks something like this:

```javascript
    const channelKey = 'gotchuu_push:' + userId;
    
		let pushPayload = {
			pn_apns: {
				aps : {
					alert: {
						title: title,  //notification title
						body:  body,  //notification custom build message
						action-loc-key: action  //action to be taken upon user checking this notification
					},
					badge: badge,  //integer value to show number of notifications
					sound: pushObj.sound
				}
			},
			data: data, //any custom object to be consumed by client; currently none.
		};
    
    
```

[//]: # (==================================================================================================)
[//]: # (==================================================================================================)