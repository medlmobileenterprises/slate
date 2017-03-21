# API Reference REST

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


