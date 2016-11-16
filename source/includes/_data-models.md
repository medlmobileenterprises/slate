# Data Models

This section is dedicated to describing all data models within this application. If there are any adjustments you see are needed, please let me know.

<aside class="notice">
	Not all fields described in these models will be included in all API responses. Each Data model described here will list all possible fields that _could_ be avaialble. Please refer to a specific API method to dertermine what fields will be accessable.
</aside>

## User

> The following samples represent examples of all the possible fields that could be returned. Excluded fields will be those that will never be returned in a response and left only to the server/database. Also note that not all fields will always be included in a response.

```json
{
	"id": "6abd8d81-c24d-41a6-bee7-db49efd2c70d",
    "createdAt": "2016-11-11T19:52:08.000Z",
    "updatedAt": "2016-11-11T19:52:08.000Z",
    "email": "thingy1@gmail.com",
    "fbId": "10207332672302279",
    "username": "catinthehat",
    "avatarFilename": "testing.jpeg",
    "avatarURL": "https://s3.amazonaws.com/gotchuu/dev/users/avatars/testing.jpeg",
    "location": {
    	"latitude": 33.123123,
    	"longitude": -113.123213
    },
    "age": 21,
    "gender": 0,
    "city": "Huntington Beach",
    "extendedBio": {
    	"bio": "I like long walks on the beach",
    	"profileImage": [
    		"image1.jpeg"
    	],
    	"profileImageURLS": [
    		"http://something.anything.com/image1.jpeg"
    	]
    }
}
```

```json-doc
{
	"id": "6abd8d81-c24d-41a6-bee7-db49efd2c70d",
    "createdAt": "2016-11-11T19:52:08.000Z",
    "updatedAt": "2016-11-11T19:52:08.000Z",
    "email": "thingy1@gmail.com",
    "fbId": "10207332672302279",
    "username": "catinthehat",
    "avatarFilename": "testing.jpeg",
    "avatarURL": "https://s3.amazonaws.com/gotchuu/dev/users/avatars/testing.jpeg",
    "location": {
    	"latitude": 33.123123,
    	"longitude": -113.123213
    },
    "age": 21,
    "gender": 0,
    "city": "Huntington Beach",
    "extendedBio": {
    	"bio": "I like long walks on the beach",
    	"profileImage": [
    		"image1.jpeg"
    	],
    	"profileImageURLS": [
    		"http://something.anything.com/image1.jpeg"
    	]
    }
}
```

| Parameter | Type | Description |
| ---- | ---- | ---- |
| id | String |  |
| createdAt | Date | Date that represents the moment the object was created in the database |
| updatedAt | Date | Date object that, if exists, represents the last time a filed in this object was updated |
| email | String | Holds the email address of the user upon registration |
| hashedPassword | String | A normally hidden field that is used to compare a password match |
| salt | String | Hidden field that is used for the hashing of the password |
| fbId | String | The facebook Id of the user upon registration |
| username | String | The username the user provided for display purposes |
| avatarFilename | String | Holds the name of the file uploaded for this user's avatar image. |
| avatarURL | String | A non-persisted field that contains a generated URL that points to the hosted avatar image |
| location | Object | A simple object that contains the `longitude` and `latitude` fields. Example: ``` { "longitude": -113.17379, "latitude":  33.32983 } ``` |
| curPoint | GeoPoint | Persisted field, but hidden from client view. This is a field used primarily by the databse to effiecintly run geospatial queries |
| birthdate | Date | Date object that represents the birthdate of the user. Used to derive the current user's age |
| age | Number | Non-persisted field that will hold the derived age value of the user based on birthdate |
| gender | Number | An enumerated value that will represent the gender of the user. Using enumerated numbers in case we need to support "gender fluidity" |
| city | String | String representation of the city the user states they reside in or originiated from |
| extendedBio | Object | An object that will represent more detailed information about a user. Visibility of this field will be bassed on the relationship between user to user. Example ``` { "bio": "I like long walks on the beach", "profileImages": ["file1.jpeg", "file2.jpeg"], "profileImageURLS": ["http://image1.jpeg", "http://image2.jpeg"] } ``` |


### User -> extendedBio

```json
{
	"bio": "I like long walks on the beach",
	"profileImage": [
		"image1.jpeg"
	],
	"profileImageURLS": [
		"http://something.anything.com/image1.jpeg"
	]    
}
```

```json-doc
{
	"bio": "I like long walks on the beach",
	"profileImage": [
		"image1.jpeg"
	],
	"profileImageURLS": [
		"http://something.anything.com/image1.jpeg"
	]    
}
```

| Parameter | Type | Description |
| ---- | ---- | ---- |
| bio | String | Long description user provides to describe themselves in words |
| profileImages | Array<String> | Persisted field of image names to represent what files the user has uploaded |
| profileImageURLS | Array<String> | Non-persisted field that is generated based off profiledImages |

### User -> location

```json
{
	"latitude": 33.123123,
	"longitude": -113.123213
}
```

```json-doc
{
	"latitude": 33.123123,
	"longitude": -113.123213
}
```

| Parameter | Type | Description |
| ---- | ---- | ---- |
| latitude | Number | Floating point number of the latitude of user's current position. Value between approx -90 & 90 |
| longitude | Number | Floating point number of the longitude of user's current position. Value between approx -180 & 180 |

