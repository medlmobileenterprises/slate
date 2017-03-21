# Data Models

This section is dedicated to describing all data models within this application. If there are any adjustments you see are needed, please let me know.

<aside class="notice">
	Not all fields described in these models will be included in all API responses. Each Data model described here will list all possible fields that _could_ be avaialble. Please refer to a specific API method to dertermine what fields will be accessable.
</aside>


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

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
    "location": {
    	"latitude": 33.123123,
    	"longitude": -113.123213
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
    "location": {
    	"latitude": 33.123123,
    	"longitude": -113.123213
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
| location | Object | A simple object that contains the `longitude` and `latitude` fields. Example: ``` { "longitude": -113.17379, "latitude":  33.32983 } ``` |
| curPoint | GeoPoint | Persisted field, but hidden from client view. This is a field used primarily by the databse to effiecintly run geospatial queries |
| inventory | Object | [InventoryModel](#inventory) |
| extendedProfile | Object | [ExtendedProfileModel](#extendedprofile) |

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


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

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
| image | String |  |
| particleColor | String |  |
| splatColor | String |  |
| bitsColor | String |  |

### Item -> particleColor, splatColor, bitsColor

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

### Item -> rarityEnum

This Enum relates to `Item`'s `rarity` field. The database will be persisting this value as a number and the API is treating this field as an ENUM. The example JSON object describes the rarity code (value) of each number (key) such that an item returned where `"rarity": 1` means that the item is related to the rarity code "C" meaning "COMMON".

```json
{
    "1": "C",
    "2": "UC",
    "3": "R",
    "4": "SR"
}
```

```json-doc
{
    "1": "C",
    "2": "UC",
    "3": "R",
    "4": "SR"
}
```

| Key | Value | Description |
| ---- | ---- | ---- |
| 1 | C | Item with `rarity: 1` is a _Common_ item |
| 2 | UC | Item with `rarity: 2` is an _UnCommon_ item |
| 3 | R | Item with `rarity: 3` is a _Rare_ item |
| 4 | SR | Item with `rarity: 4` is a _SuperRare_ item |

### Item -> typeEnum

This Enum relates to `Item`'s `type` field. The database will be persisting this value as a number which the table and example JSON decribe the value that each number represents.

```json
{
    "0": "Fruits & Veggies",
    "1": "Meats",
    "2": "Alternatives",
    "3": "Grains",
    "4": "Herbs & Spices"
}
```

```json-doc
{
    "0": "Fruits & Veggies",
    "1": "Meats",
    "2": "Alternatives",
    "3": "Grains",
    "4": "Herbs & Spices"
}
```

| Key | Value | Description |
| ---- | ---- | ---- |
| 0 | Fruits & Veggies | Item with `type: 0` is a _Fruits & Veggies_ item |
| 1 | Meats | Item with `type: 1` is a _Meats_ item |
| 2 | Alternatives | Item with `type: 2` is an _Alternatives_ item |
| 3 | Grains | Item with `type: 3` is a _Grains_ item |
| 4 | Herbs & Spices | Item with `type: 4` is a _Herbs & Spices_ item |

### Item -> animType

This Enum relates to `Item`'s `animType` field. The database will be persisting this value as a number which the table and example JSON decribe the value that each number represents.
___This Enum still needs to be defined as this will be a value the client app is supposed to use for assets saved on the installation___
```json
{
    "0": "Splat1"
}
```

```json-doc
{
    "0": "Splat1"
}
```

| Key | Value | Description |
| ---- | ---- | ---- |
| 0 | Splat1 | Item with `animType: 0` will use the _Splat1_ animation |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Inventory

> The following samples represent examples of all the possible fields that could be returned. Excluded fields will be those that will never be returned in a response and left only to the server/database. Also note that not all fields will always be included in a response.

```json
{
    "baseInvCount": 75,
    "createdAt":  "2016-12-10T03:37:36.566Z",
    "id":  "c6aad8c0-fac2-4112-9f39-24861c7f5a9d",
    "level": 1,
    "userId":  "d3b0a471-eb99-42a6-9d87-76299abfd64a"
}
```

```json-doc
{
    "baseInvCount": 75 ,
    "createdAt":  "2016-12-10T03:37:36.566Z",
    "id":  "c6aad8c0-fac2-4112-9f39-24861c7f5a9d",
    "level": 1,
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


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## InventoryItem

This table is what can be called an *Auxiliary* table which serves the purpose of linking static data to dynamic logic. Since an inventory can have duplicates of the same ___Item___, this table helps to make duplicates of the same ___Item___ unique in a user's inventory space.

> The following samples represent examples of all the possible fields that could be returned. Excluded fields will be those that will never be returned in a response and left only to the server/database. Also note that not all fields will always be included in a response.

```json
{
    "active": true ,
    "createdAt": "2016-12-10T03:37:36.574Z",
    "id":  "1ce2ede0-57c1-46ad-8a15-dc1c9d9e3293",
    "invId":  "c6aad8c0-fac2-4112-9f39-24861c7f5a9d",
    "itemId":  "9a3cd94d-79d2-4378-a011-fb68c139191b"
}
```

```json-doc
{
    "active": true ,
    "createdAt": "2016-12-10T03:37:36.574Z",
    "id":  "1ce2ede0-57c1-46ad-8a15-dc1c9d9e3293",
    "invId":  "c6aad8c0-fac2-4112-9f39-24861c7f5a9d",
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


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## DropItem

This table is what can be called an *Auxiliary* table which serves the purpose of linking static data to dynamic logic. This table will ensure that the `pickupItem` method is only allowing a user to pickup items that have spawned for them.

> The following samples represent examples of all the possible fields that could be returned. Excluded fields will be those that will never be returned in a response and left only to the server/database. Also note that not all fields will always be included in a response.

```json
{
    "createdAt": "2016-12-10T03:37:36.574Z",
    "id":  "a3224d31-db6c-4780-8dfe-d0c61f5cc8a6",
    "itemId":  "b03e33cd-9441-4cfe-9f90-631fd650fffd",
    "userId":  "d3b0a471-eb99-42a6-9d87-76299abfd64a"
}
```

```json-doc
{
    "createdAt": "2016-12-10T03:37:36.574Z",
    "id":  "a3224d31-db6c-4780-8dfe-d0c61f5cc8a6",
    "itemId":  "b03e33cd-9441-4cfe-9f90-631fd650fffd",
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


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Engagement

Description for this model

> The following samples represent examples of all the possible fields that could be returned. Excluded fields will be those that will never be returned in a response and left only to the server/database. Also note that not all fields will always be included in a response.

```json
{
    "id": "b03e33cd-9441-4cfe-9f90-631fd650fffd",
    "createdAt":  "2016-12-10T03:37:36.574Z",
    "updatedAt":  "2016-12-10T03:37:36.574Z",
    "fromUId":  "d3b0a471-eb99-42a6-9d87-76299abfd64a",
    "toUId":  "d3b0a471-eb99-42a6-9d87-76299abfd64a",
    "status":  0,
    "hits":  0,
    "misses":  0,
    "win":  false
}
```

```json-doc
{
    "id": "b03e33cd-9441-4cfe-9f90-631fd650fffd",
    "createdAt":  "2016-12-10T03:37:36.574Z",
    "updatedAt":  "2016-12-10T03:37:36.574Z",
    "fromUId":  "d3b0a471-eb99-42a6-9d87-76299abfd64a",
    "toUId":  "d3b0a471-eb99-42a6-9d87-76299abfd64a",
    "status":  0,
    "hits":  0,
    "misses":  0,
    "win":  false
}
```

| Parameter | Type | Description |
| ---- | ---- | ---- |
| id | String | Uniquely generated Id for the object |
| createdAt | Date |  |
| updatedAt | Date | This field will always contain the most recent date the object was modified |
| fromUId | String | Contains the userId who initiated/started the engagement |
| toUId | String | Contains the userId of the victim of the engagement |
| status | Number | An enum value to determine what the state of the engagement is |
| hits | Number | A count of successful hits |
| misses | Number | A count of the missed throws |
| win | Boolean | Determines if this engagement was a success or not |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Relationship

Description for this model

> The following samples represent examples of all the possible fields that could be returned. Excluded fields will be those that will never be returned in a response and left only to the server/database. Also note that not all fields will always be included in a response.

```json
{
    "id": "d3b0a471-eb99-42a6-9d87-76299abfd64a",
    "createdAt":  "2016-12-10T03:37:36.574Z",
    "updatedAt":  "2016-12-10T03:37:36.574Z",
    "channelName":  "unique-user-id-1_unique-user-id-2",
    "lastInitiator":  "unique-user-id-1",
    "points":  0,
    "level":  0,
    "userIds": [
        "unique-user-id-1",
        "unique-user-id-2"
    ]
}
```

```json-doc
{
    "id": "d3b0a471-eb99-42a6-9d87-76299abfd64a",
    "createdAt":  "2016-12-10T03:37:36.574Z",
    "updatedAt":  "2016-12-10T03:37:36.574Z",
    "channelName":  "unique-user-id-1_unique-user-id-2",
    "lastInitiator":  "unique-user-id-1",
    "points":  0,
    "level":  0,
    "userIds": [
        "unique-user-id-1",
        "unique-user-id-2"
    ]
}
```

| Parameter | Type | Description |
| ---- | ---- | ---- |
| id | String | Uniquely generated Id for the object |
| createdAt | Date |  |
| updatedAt | Date | This field will always contain the most recent date the object was modified |
| channelName | String | Genereated by the server upon initialization of the relationship. It is a unique channel name for the two users and kept so by simply concatentating the userIds appointed to this relationship, delimited by the underscore '_' character. |
| lastInitiator | String | This represents the last user to have modified/challenged the other user in the relationship. This field will be null after a successful response from the challenged user |
| points | Number | A simple counter of successful back-and-forth responses from the two users. After ever 2 points, a level is gained |
| level | Number | Contains the level of the current relationship |
| userIds | Array | Conatins an array of strings representing the userIds of the two user's |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## ItemUsed

Description for this model

> The following samples represent examples of all the possible fields that could be returned. Excluded fields will be those that will never be returned in a response and left only to the server/database. Also note that not all fields will always be included in a response.

```json
{
    "id": "d3b0a471-eb99-42a6-9d87-76299abfd64a",
    "createdAt":  "2016-12-10T03:37:36.574Z",
    "updatedAt":  "2016-12-10T03:37:36.574Z",
    "engagementId":  "unique-engagement-id",
    "userId":  "unique-user-id",
    "itemId":  "unique-item-id"
}
```

```json-doc
{
    "id": "d3b0a471-eb99-42a6-9d87-76299abfd64a",
    "createdAt":  "2016-12-10T03:37:36.574Z",
    "updatedAt":  "2016-12-10T03:37:36.574Z",
    "engagementId":  "unique-engagement-id",
    "userId":  "unique-user-id",
    "itemId":  "unique-item-id"
}
```

| Parameter | Type | Description |
| ---- | ---- | ---- |
| id | String | Uniquely generated Id for the object |
| createdAt | Date |  |
| updatedAt | Date |  |
| engagementId | String | The engagement that this item was used in |
| userId | String | The userId of the one who used the item |
| itemId | String | The itemId of the item which was used for details on the item |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## ExtendedProfile

Additional user information that is accessible based on certain properties on relationships

> The following samples represent examples of all the possible fields that could be returned. Excluded fields will be those that will never be returned in a response and left only to the server/database. Also note that not all fields will always be included in a response.

```json
{
    "id": "d3b0a471-eb99-42a6-9d87-76299abfd64a",
    "createdAt": "2016-12-10T03:37:36.574Z",
    "updatedAt": "2016-12-10T03:37:36.574Z",
    "bio": "Some type of description of one's self",
    "inches": 60,
    "age": 21,
    "birthdate": "2016-12-10T03:37:36.574Z",
    "city": "Nowhere City",
    "gender": 0,
    "userId": "unique-item-id"
}
```

```json-doc
{
    "id": "d3b0a471-eb99-42a6-9d87-76299abfd64a",
    "createdAt": "2016-12-10T03:37:36.574Z",
    "updatedAt": "2016-12-10T03:37:36.574Z",
    "bio": "Some type of description of one's self",
    "inches": 60,
    "age": 21,
    "birthdate": "2016-12-10T03:37:36.574Z",
    "city": "Nowhere City",
    "gender": 0,
    "userId": "unique-item-id"
}
```

| Parameter | Type | Description |
| ---- | ---- | ---- |
| id | String | Uniquely generated Id for the object |
| createdAt | Date |  |
| updatedAt | Date |  |
| bio | String | This is a plain string that the user enters to describe themselves |
| inches | Number | This will represent the user's height in inches. |
| age | Number | A number to represent the user's age |
| birthdate | Date | A date value that represents the date the user would have been born. This value could be used to dynamically update the user's age value. |
| city | String | A string value to represent the name of the city the user comes from |
| gender | Number | A simple number enumerator to represent a gender type: `Male = 0; Female = 1` |
| userId | String | The unique id of the user who owns this extended profile |
| profileImages | Object[] | A list of [FileUploads](#fileupload) that the user uploaded for their profile. |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## FileUpload

This is the object representation of the file that was uploaded for a give user.

> The following samples represent examples of all the possible fields that could be returned. Excluded fields will be those that will never be returned in a response and left only to the server/database. Also note that not all fields will always be included in a response.

```json
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
```

```json-doc
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
```

| Parameter | Type | Description |
| ---- | ---- | ---- |
| id | String | Uniquely generated Id for the object |
| createdAt | Date |  |
| updatedAt | Date |  |
| extendedProfileId | String | This is the unique id of a user's extended profile that his file should be associated with |
| fileExt | String | This is the file extension that was found for the file uploaded. Used in the generation of the imageUrl |
| filename | String | The original name of the file that was uploaded. |
| isProfile | Boolean | A boolean value to represnt that this file uploaded should represent the user's main profile picture |
| order | Number | An arbitrary value to use in case we need to implement arbitrary ordering of images |
| userId | String | The unique user id of the user who owns this file |
| imageUrl | String | A generated url field that will point to the current hosted location of the file |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Chat

This is the object representation of Chat messages stored in the database

> The following samples represent examples of all the possible fields that could be returned. Excluded fields will be those that will never be returned in a response and left only to the server/database. Also note that not all fields will always be included in a response.

```json
{
    "channelName": "f33ceb35-9847-4d1d-a3d2-dd1649661657_d3b0a471-eb99-42a6-9d87-76299abfd64a",
    "createdAt": "2017-02-25T08:33:48.387Z",
    "fromUId": "f33ceb35-9847-4d1d-a3d2-dd1649661657",
    "id": "32d3f620-0a4f-4fb2-ae3b-1475df1b05af",
    "message": "Hello world",
    "read": false,
    "timeStamp": "2017-02-25T08:33:48.365Z",
    "toUId": "d3b0a471-eb99-42a6-9d87-76299abfd64a"
}
```

```json-doc
{
    "channelName": "f33ceb35-9847-4d1d-a3d2-dd1649661657_d3b0a471-eb99-42a6-9d87-76299abfd64a",
    "createdAt": "2017-02-25T08:33:48.387Z",
    "fromUId": "f33ceb35-9847-4d1d-a3d2-dd1649661657",
    "id": "32d3f620-0a4f-4fb2-ae3b-1475df1b05af",
    "message": "Hello world",
    "read": false,
    "timeStamp": "2017-02-25T08:33:48.365Z",
    "toUId": "d3b0a471-eb99-42a6-9d87-76299abfd64a"
}
```

| Parameter | Type | Description |
| ---- | ---- | ---- |
| id | String | Uniquely generated Id for the object. |
| createdAt | Date |  |
| updatedAt | Date |  |
| channelName | String | Represents the name of the pubnub channel users should subscribe to receive messages. |
| fromUId | String | The sender of the message. |
| toUId | String | The receiver of the message. |
| message | String | The contents of the message |
| read | Boolean | This is the status of the message for the `toUser`. This fields helps to determine if a user has any unread messages and if their conversation should be badged or not. |
| timeStamp | Date | This is the moment in time that the message was sent. This will help to order and paginate any response to get a list of past messages |

[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Notification

This is the object representation of Notifications stored in the database for each User.
Expected to be created for a user as soon they are registered with our app.

> The following samples represent examples of all the possible fields that could be returned. Excluded fields will be those that will never be returned in a response and left only to the server/database. Also note that not all fields will always be included in a response.

```json
{
    "channelKey": "e59b23b9-abcd-4241-a405-097cc2ba50e9_somekey",
    "userId": "e59b23b9-abcd-4241-a405-097cc2ba50e9",
    "createdAt": "2017-03-21T01:08:59.976Z",
    "id": "84e4257c-b84e-46dd-a43c-356774069ca0"
}
```

```json-doc
{
    "channelKey": "e59b23b9-abcd-4241-a405-097cc2ba50e9_somekey",
    "userId": "e59b23b9-abcd-4241-a405-097cc2ba50e9",
    "createdAt": "2017-03-21T01:08:59.976Z",
    "id": "84e4257c-b84e-46dd-a43c-356774069ca0"
}
```

| Parameter | Type | Description |
| ---- | ---- | ---- |
| id | String | Uniquely generated Id for the object. |
| createdAt | Date |  |
| updatedAt | Date |  |
| channelKey | String | Represents the name of the pubnub channel user should subscribe to receive notifications. |
| userId | String | User associated with this channelkey. |

[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Block

This is the object representation of Blocks stored in the database between two Users.
Expected to be created for a user as soon they are registered with our app.

> The following samples represent examples of all the possible fields that could be returned. Excluded fields will be those that will never be returned in a response and left only to the server/database. Also note that not all fields will always be included in a response.

```json
{
    "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
    "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab",
    "createdAt": "2017-03-21T17:47:59.551Z",
    "id": "c4d88db5-09f9-4970-977a-a417e0d9e369"
  }
```

```json-doc
{
    "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
    "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab",
    "createdAt": "2017-03-21T17:47:59.551Z",
    "id": "c4d88db5-09f9-4970-977a-a417e0d9e369"
  }
```

| Parameter | Type | Description |
| ---- | ---- | ---- |
| id | String | Uniquely generated Id for the object. |
| createdAt | Date |  |
| updatedAt | Date |  |
| fromUId | String | User who iniciated the block. |
| toUId | String | User getting blocked. |


[//]: # (==================================================================================================)
[//]: # (==================================================================================================)

## Reported

This is the represntation of the `Report` object in the database. 

> The following samples represent examples of all the possible fields that could be returned. Excluded fields will be those that will never be returned in a response and left only to the server/database. Also note that not all fields will always be included in a response.

```json
{
    "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
    "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab",
    "status": 1,
    "reason": 1,
    "createdAt": "2017-03-21T18:39:26.495Z",
    "id": "c3105b78-61e1-48a4-ba95-30eb8df7d514"
  }
```

```json-doc
{
    "fromUId": "45dcb0a4-38d2-4381-a4ea-f5d866445038",
    "toUId": "81cd8e07-3031-42de-9f30-b71b40d7eaab",
    "status": 1,
    "reason": 1,
    "createdAt": "2017-03-21T18:39:26.495Z",
    "id": "c3105b78-61e1-48a4-ba95-30eb8df7d514"
  }
```

| Parameter | Type | Description |
| ---- | ---- | ---- |
| id | String | Uniquely generated Id for the object. |
| createdAt | Date |  |
| updatedAt | Date |  |
| fromUId | String | User who is reporting another user. |
| toUId | String | User who is the target for the Report. |
| status | Number | An enumeration value representing the status of this Report. Should be used as a way to determine if the report has been reviewed or not and possibly to determine the action taken from this report. |
| reason | Number | **Optional** An enumeration value to represent the reason for this report. |
| fromUser | Object<[User](#user)> | This could be included in the model when returned by the API. This would be the object representation of the user who created the report against another user. |
| toUser | Object<[User](#user)> | This could be included in the model when returned by the API. This would be the object representation of the user who is the subject of the report. |

### Report Status codes

| Code | Description |
| ---- | ---- |
| 1 | PENDING |
| 1000 | OKAY |

