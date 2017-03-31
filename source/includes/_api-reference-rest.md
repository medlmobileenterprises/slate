# API Reference REST

All endpoints will resolve with the following host (domain) name/address:

`http://gotcha-dev.us-east-1.elasticbeanstalk.com`


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Users

[//]: # (==================================================================================================)
### Upload Profile Image

```json
"RPC method not supported for this type of function"
```

```json
```

```json-doc
"POST /api/users/:unique-user-id/upload-avatar HTTP/1.1 Content-Type: multipart/form-data"
```

> The above command returns JSON structured like this:

```json
```

```json-doc
{
  "success": true,
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
        },
        {
          "createdAt": "2017-02-14T01:31:34.267Z",
          "extendedProfileId": "c1d01481-920b-444b-a733-21ee6fa2af69",
          "fileExt": ".png",
          "filename": "hylian_shield",
          "id": "0f4a40ae-14d6-4c24-b3c1-dccb535249be",
          "isProfile": false,
          "order": 0,
          "updatedAt": "2017-02-14T18:46:36.564Z",
          "userId": "fe883474-f89c-4d60-9017-4f5a7d3bbef2",
          "imageUrl": "https://s3.amazonaws.com/gotchuu/dev/users/profileImages/fe883474-f89c-4d60-9017-4f5a7d3bbef2/0f4a40ae-14d6-4c24-b3c1-dccb535249be.png"
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

This method is used to upload a profile image for a user. This method can only be made through a RESTful POST call using the `Content-Type: multipart/form-data` header. The only field that needs to be sent as form data is the `avatar` field with the value of the file to be uploading in multipart fashion. If successful, the response will contain the full user profile with the newly added [FileUpload](#fileupload) object representing the new upload among any others that have already been uploaded, all containing their respective `imageUrl` fields already generated.

#### RESTful path
`/api/users/:userId/upload-avatar`

#### Form Data Fields

| Parameter | Type | Description |
| ---- | ---- | ---- |
| fileUploadId | String | **Optional** The unique fileUploadId from the user's list of profileImages to update with the new image. Only use this if we are going to support replacing a file instead of Deleting the file first then creating a new one. |
| avatar | File | **REQUIRED** The unique fileUploadId from the user's list of profileImages to promote to the main profile image. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| success | Boolean | If successful, this value will be true |
| result | [User](#user) | Upon success, the result will contain the full [User](#user) object with the [ExtendedProfile](#extendedprofile) in the `extendedProfile` field and inside this object will be a list of `profileImages` with [FileUpload](#fileupload) as their object representation |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)
### Delete a User's image

```json
"RPC method not supported for this type of function"
```

```json
```

```json-doc
"PUT /api/users/deleteAnImage"
```

> The above command returns JSON structured like this:

```json
```

```json-doc

```

This method will remove a profile image from a users extended profile and delete the image from the cloud storage location.

#### RESTful path
`/api/users/deleteAnImage`

#### Form Data Fields

| Parameter | Type | Description |
| ---- | ---- | ---- |
| userId | String | user id   |
| fileId | String | id of the file to be deleted. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| success | Boolean | If successful, this value will be true |
| result | [User](#user) | Returns a user object with profile information |

[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Reports

[//]: # (==================================================================================================)
### Get Reported User

```json
"RPC method not supported for this type of function"
```

```json
```

```json-doc
"GET /api/report/:fromUId/:toUId/getReport"
```

> The above command returns JSON structured like this:

```json
```

```json-doc
{
  "success": true,
  "result": [
    {
      "createdAt": "2017-03-21T18:39:26.495Z",
      "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
      "id": "c3105b78-61e1-48a4-ba95-30eb8df7d514",
      "reason": 1,
      "status": 1,
      "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab"
    }
  ]
}
```

This method gets a specific desired report from the db.

#### RESTful path
`/api/report/:fromUId/:toUId/getReport`

#### Form Data Fields

| Parameter | Type | Description |
| ---- | ---- | ---- |
| fromUId | String | user id initiated reporting |
| toUId | String | user being reported |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| success | Boolean | If successful, this value will be true |
| result | Array | Report Model Object |

[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

### Get Reported User's reason count

```json
"RPC method not supported for this type of function"
```

```json
```

```json-doc
"GET /api/report/:userId/eachUserReportCount"
```

> The above command returns JSON structured like this:

```json
```

```json-doc
{
  "success": true,
  "result": [
    {
      "reason": 1,
      "reasonCount": 3
    },
    {
      "reason": 2,
      "reasonCount": 2
    },
    {
      "reason": 3,
      "reasonCount": 9
    }
  ]
}
```

This method gets a specific desired report from the db.

#### RESTful path
`/api/report/:userId/eachUserReportCount`

#### Form Data Fields

| Parameter | Type | Description |
| ---- | ---- | ---- |
| userId | String | ID of the report client is seraching for. |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| success | Boolean | If successful, this value will be true |
| result | Array | Report Model Object |

[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

### Get All Reports

```json
"RPC method not supported for this type of function"
```

```json
```

```json-doc
"GET /api/report/getAllOpenReports"
```

> The above command returns JSON structured like this:

```json
```

```json-doc
{
  "success": true,
  "result": [
    {
      "reportedUser": "81cd8e07-3031-42de-9f30-b71b40d7eaab",
      "reports": [
        {
          "createdAt": "2017-03-24T22:40:05.660Z",
          "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
          "id": "d537c451-bfe4-42c4-bdd8-6bf9b52ce9a0",
          "reason": 3,
          "status": 1,
          "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab",
          "toUser": {
            "banned": false,
            "city": "irvine",
            "createdAt": "2017-01-03T23:10:03.004Z",
            "email": "ankit@uci.edu",
            "id": "81cd8e07-3031-42de-9f30-b71b40d7eaab",
            "username": "ankit",
            "itemLevel": 1,
            "ftueComplete": false,
            "badge": 0
          }
        },
        {
          "createdAt": "2017-03-24T22:40:05.414Z",
          "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
          "id": "20596f6d-d99d-4939-b2a5-82e1fd7ea039",
          "reason": 3,
          "status": 1,
          "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab",
          "toUser": {
            "banned": false,
            "city": "irvine",
            "createdAt": "2017-01-03T23:10:03.004Z",
            "email": "ankit@uci.edu",
            "id": "81cd8e07-3031-42de-9f30-b71b40d7eaab",
            "username": "ankit",
            "itemLevel": 1,
            "ftueComplete": false,
            "badge": 0
          }
        }
      ],
      "reportsCount": 2
    }
  ]
}
```

This method gets all the reports in db.

#### RESTful path
`/api/report/getAllOpenReports`

#### Form Data Fields

| Parameter | Type | Description |
| ---- | ---- | ---- |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| success | Boolean | If successful, this value will be true |
| result | Array | Report Model Object |

[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

### Get All Reports by user reported.

```json
"RPC method not supported for this type of function"
```

```json
```

```json-doc
"GET /api/report/:toUId/userReportedBy"
```

> The above command returns JSON structured like this:

```json
```

```json-doc
{
  "success": true,
  "result": [
    {
      "createdAt": "2017-03-21T18:39:26.495Z",
      "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
      "id": "c3105b78-61e1-48a4-ba95-30eb8df7d514",
      "reason": 1,
      "status": 1,
      "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab"
    },
    {
          "createdAt": "2017-03-21T18:39:26.495Z",
          "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
          "id": "c3105b78-61e1-48a4-ba95-30eb8df7d514",
          "reason": 1,
          "status": 1,
          "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab"
     }
  ]
}
```

This method gets all the reports in db for reported user that being toUId 

#### RESTful path
`/api/report/:toUId/userReportedBy`

#### Form Data Fields

| Parameter | Type | Description |
| ---- | ---- | ---- |
| toUId | String | user being reported |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| success | Boolean | If successful, this value will be true |
| result | Array | Report Model Object |

[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

### Get All Reports by user reporting another user.

```json
"RPC method not supported for this type of function"
```

```json
```

```json-doc
"GET /api/report/:fromUId/userReportedList"
```

> The above command returns JSON structured like this:

```json
```

```json-doc
{
  "success": true,
  "result": [
    {
      "createdAt": "2017-03-21T18:39:26.495Z",
      "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
      "id": "c3105b78-61e1-48a4-ba95-30eb8df7d514",
      "reason": 1,
      "status": 1,
      "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab"
    },
    {
          "createdAt": "2017-03-21T18:39:26.495Z",
          "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
          "id": "c3105b78-61e1-48a4-ba95-30eb8df7d514",
          "reason": 1,
          "status": 1,
          "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab"
     }
  ]
}
```

This method gets all the reports in db for user who reported other users.

#### RESTful path
`/api/report/:fromUId/userReportedList`

#### Form Data Fields

| Parameter | Type | Description |
| ---- | ---- | ---- |
| fromUId | String | user reporting |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| success | Boolean | If successful, this value will be true |
| result | Array | Report Model Object |

[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

### Get Report by Id.

```json
"RPC method not supported for this type of function"
```

```json
```

```json-doc
"GET /api/report/:reportId/fetchUserReported"
```

> The above command returns JSON structured like this:

```json
```

```json-doc
{
  "success": true,
  "result": 
    {
      "createdAt": "2017-03-21T18:39:26.495Z",
      "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
      "id": "c3105b78-61e1-48a4-ba95-30eb8df7d514",
      "reason": 1,
      "status": 1,
      "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab"
    }
}
```

This method gets all the reports in db for user who reported other users.

#### RESTful path
`/api/report/:reportId/fetchUserReported`

#### Form Data Fields

| Parameter | Type | Description |
| ---- | ---- | ---- |
| reportId | String | report id |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| success | Boolean | If successful, this value will be true |
| result | Object | Report Model Object |

[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

### Update report status

```json
"RPC method not supported for this type of function"
```

```json
```

```json-doc
"PUT /api/report/:reportId/updateStatus/:status"
```

> The above command returns JSON structured like this:

```json
```

```json-doc
{
  "success": true,
  "result": 
    {
      "createdAt": "2017-03-21T18:39:26.495Z",
      "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
      "id": "c3105b78-61e1-48a4-ba95-30eb8df7d514",
      "reason": 1,
      "status": 2,
      "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab"
    }
}
```

This method updates the status of a given report.

#### RESTful path
`/api/report/:reportId/updateStatus/:status`

#### Form Data Fields

| Parameter | Type | Description |
| ---- | ---- | ---- |
| reportId | String | report id |
| status | Integer | current status of this report |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| success | Boolean | If successful, this value will be true |
| result | Object | Updated Report Model Object |

[//]: # (==================================================================================================)
[//]: # (==================================================================================================)



## Banning

[//]: # (==================================================================================================)

### Ban a User

```json
"RPC method not supported for this type of function"
```

```json
```

```json-doc
"GET /api/ban/:userId/banUser"
```

> The above command returns JSON structured like this:

```json
```

```json-doc
{
  "success": true,
  "result": {
    "banned": true,
    "city": "irvine",
    "createdAt": "2017-01-03T23:10:03.004Z",
    "email": "ankit@uci.edu",
    "id": "81cd8e07-3031-42de-9f30-b71b40d7eaab",
    "username": "ankit",
    "ftueComplete": false,
    "badge": 0
  }
}
```

This method gets a specific desired report from the db.

#### RESTful path
`/api/ban/:userId/banUser`

#### Form Data Fields

| Parameter | Type | Description |
| ---- | ---- | ---- |
| userId | String | user id to be banned |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| success | Boolean | If successful, this value will be true |
| result | Object | User Model Object |

[//]: # (==================================================================================================)
[//]: # (==================================================================================================)


### Un Ban a User

```json
"RPC method not supported for this type of function"
```

```json
```

```json-doc
"GET /api/ban/:userId/unbanUser"
```

> The above command returns JSON structured like this:

```json
```

```json-doc
{
  "success": true,
  "result": {
    "banned": false,
    "city": "irvine",
    "createdAt": "2017-01-03T23:10:03.004Z",
    "email": "ankit@uci.edu",
    "id": "81cd8e07-3031-42de-9f30-b71b40d7eaab",
    "username": "ankit",
    "ftueComplete": false,
    "badge": 0
  }
}
```

This method gets a specific desired report from the db.

#### RESTful path
`/api/ban/:userId/unbanUser`

#### Form Data Fields

| Parameter | Type | Description |
| ---- | ---- | ---- |
| userId | String | user id  getting un banned |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| success | Boolean | If successful, this value will be true |
| result | Object | User Model Object |

[//]: # (==================================================================================================)
[//]: # (==================================================================================================)



## Extended Profile

[//]: # (==================================================================================================)
### Get a User's Extended Profile

```json
"RPC method not supported for this type of function"
```

```json
```

```json-doc
"GET /api/extendedProfile/:userId/extendedProfile"
```

> The above command returns JSON structured like this:

```json
```

```json-doc
{
  "success": true,
  "result": {
    "banned": false,
    "city": "irvine",
    "createdAt": "2017-01-03T23:10:03.004Z",
    "email": "ankit@uci.edu",
    "id": "81cd8e07-3031-42de-9f30-b71b40d7eaab",
    "username": "ankit",
    "itemLevel": 1,
    "ftueComplete": false,
    "badge": 0
  }
}
```

This method gets a specific desired report from the db.

#### RESTful path
`/api/extendedProfile/:userId/extendedProfile`

#### Form Data Fields

| Parameter | Type | Description |
| ---- | ---- | ---- |
| userId | String | user id of the needed extended profile |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| success | Boolean | If successful, this value will be true |
| result | Array | Extended Profile Model Object |

[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

### Update a User's Extended Profile

```json
"RPC method not supported for this type of function"
```

```json
```

```json-doc
"PUT /api/extendedProfile/:userId/updateProfile"
```

> The above command returns JSON structured like this:

```json
```

```json-doc
{
  "success": true,
  "result": {
    "banned": false,
    "city": "irvine",
    "createdAt": "2017-01-03T23:10:03.004Z",
    "email": "ankit@uci.edu",
    "id": "81cd8e07-3031-42de-9f30-b71b40d7eaab",
    "username": "ankit",
    "itemLevel": 1,
    "ftueComplete": false,
    "badge": 0
  }
}
```

This method gets a specific desired report from the db.

#### RESTful path
`/api/extendedProfile/:userId/updateProfile`

#### Form Data Fields

| Parameter | Type | Description |
| ---- | ---- | ---- |
| userId | String | user id of the updating extended profile |

#### Response Attributes

| Parameter | Type | Description |
| ---- | ---- | ---- |
| success | Boolean | If successful, this value will be true |
| result | Array | Extended Profile Model Object |

[//]: # (==================================================================================================)
[//]: # (==================================================================================================)