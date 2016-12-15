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
| avatarUpdatedAt | Date |  |
| inventory | Object | [InventoryModel](#inventory) |


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


## Item

> The following samples represent examples of all the possible fields that could be returned. Excluded fields will be those that will never be returned in a response and left only to the server/database. Also note that not all fields will always be included in a response.

```json
{
    "animType": 0 ,
    "createdAt":  "2016-12-10T03:37:36.574Z" ,
    "damage":  "XS" ,
    "description":  "I hab a peeen" ,
    "id":  "b03e33cd-9441-4cfe-9f90-631fd650fffd" ,
    "name":  "Pen" ,
    "rarity": 1 ,
    "type": 0,
    "animColor": {
        "r": 255,
        "g": 255,
        "b": 255
    }
}
```

```json-doc
{
    "animType": 0 ,
    "createdAt":  "2016-12-10T03:37:36.574Z" ,
    "damage":  "XS" ,
    "description":  "I hab a peeen" ,
    "id":  "b03e33cd-9441-4cfe-9f90-631fd650fffd" ,
    "name":  "Pen" ,
    "rarity": 1 ,
    "type": 0,
    "animColor": {
        "r": 255,
        "g": 255,
        "b": 255
    }
}
```

| Parameter | Type | Description |
| ---- | ---- | ---- |
| animType | Number |  |
| createdAt | Date |  |
| updatedAt | Date |  |
| damage | String |  |
| description | String |  |
| id | String |  |
| name | String |  |
| rarity | Number |  |
| type | Number |  |
| animColor | Object |  |

### Item -> animColor

```json
{
    "r": 255,
    "g": 255,
    "b": 255
}
```

```json-doc
{
    "r": 255,
    "g": 255,
    "b": 255
}
```

| Parameter | Type | Description |
| ---- | ---- | ---- |
| r | Number |  |
| g | Number |  |
| b | Number |  |


## Inventory

> The following samples represent examples of all the possible fields that could be returned. Excluded fields will be those that will never be returned in a response and left only to the server/database. Also note that not all fields will always be included in a response.

```json
{
    "baseInvCount": 75 ,
    "createdAt":  "2016-12-10T03:37:36.566Z" ,
    "id":  "c6aad8c0-fac2-4112-9f39-24861c7f5a9d" ,
    "level": 1 ,
    "userId":  "d3b0a471-eb99-42a6-9d87-76299abfd64a"
}
```

```json-doc
{
    "baseInvCount": 75 ,
    "createdAt":  "2016-12-10T03:37:36.566Z" ,
    "id":  "c6aad8c0-fac2-4112-9f39-24861c7f5a9d" ,
    "level": 1 ,
    "userId":  "d3b0a471-eb99-42a6-9d87-76299abfd64a"
}
```

| Parameter | Type | Description |
| ---- | ---- | ---- |
| baseInvCount | Number | Value that initializes the base/standard amount of inventory space |
| createdAt | Date |  |
| updatedAt | Date |  |
| id | String |  |
| level | Number | To be used later to "expand" the inventory space |
| userId | String | A reference to the unique-id of the owner of this inventory |


## InventoryItem

This table is what can be called an *Auxiliary* table which serves the purpose of linking static data to dynamic logic. Since an inventory can have duplicates of the same ___Item___, this table helps to make duplicates of the same ___Item___ unique in a user's inventory space.

> The following samples represent examples of all the possible fields that could be returned. Excluded fields will be those that will never be returned in a response and left only to the server/database. Also note that not all fields will always be included in a response.

```json
{
    "active": true ,
    "createdAt": Wed Dec 14 2016 22:01:59 GMT+00:00 ,
    "id":  "1ce2ede0-57c1-46ad-8a15-dc1c9d9e3293" ,
    "invId":  "c6aad8c0-fac2-4112-9f39-24861c7f5a9d" ,
    "itemId":  "9a3cd94d-79d2-4378-a011-fb68c139191b"
}
```

```json-doc
{
    "active": true ,
    "createdAt": Wed Dec 14 2016 22:01:59 GMT+00:00 ,
    "id":  "1ce2ede0-57c1-46ad-8a15-dc1c9d9e3293" ,
    "invId":  "c6aad8c0-fac2-4112-9f39-24861c7f5a9d" ,
    "itemId":  "9a3cd94d-79d2-4378-a011-fb68c139191b"
}
```

| Parameter | Type | Description |
| ---- | ---- | ---- |
| active | Boolean | Possibly used later to keep item in inventory but make unusable? |
| createdAt | Date |  |
| updatedAt | Date |  |
| id | String |  |
| invId | String | Unique ID reference to the inventory this item should be associated with |
| itemId | String | Unique ID reference to the item details |


## DropItem

This table is what can be called an *Auxiliary* table which serves the purpose of linking static data to dynamic logic. This table will ensure that the `pickupItem` method is only allowing a user to pickup items that have spawned for them.

> The following samples represent examples of all the possible fields that could be returned. Excluded fields will be those that will never be returned in a response and left only to the server/database. Also note that not all fields will always be included in a response.

```json
{
    "createdAt": Wed Dec 14 2016 22:01:03 GMT+00:00 ,
    "id":  "a3224d31-db6c-4780-8dfe-d0c61f5cc8a6" ,
    "itemId":  "b03e33cd-9441-4cfe-9f90-631fd650fffd" ,
    "userId":  "d3b0a471-eb99-42a6-9d87-76299abfd64a"
}
```

```json-doc
{
    "createdAt": Wed Dec 14 2016 22:01:03 GMT+00:00 ,
    "id":  "a3224d31-db6c-4780-8dfe-d0c61f5cc8a6" ,
    "itemId":  "b03e33cd-9441-4cfe-9f90-631fd650fffd" ,
    "userId":  "d3b0a471-eb99-42a6-9d87-76299abfd64a"
}
```

| Parameter | Type | Description |
| ---- | ---- | ---- |
| createdAt | Date |  |
| updatedAt | Date |  |
| id | String |  |
| itemId | String | Unique ID reference to the item details |
| userId | String | Unique ID reference to the user that is allowed to claim this item |

