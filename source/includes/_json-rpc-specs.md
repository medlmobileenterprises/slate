# JSON-RPC 2.0 Specifications

As of now, the Gotchuu API will be utilizing the JSON RPC 2.0 specification over HTTP as the basis of communication. This gives us a few benefits over a RESTful API.

1. More consistency in the method that calls are made
2. Greater consistency in how the request and response bodys are constructed
3. Functional over Resource, meaning the server call feels more like calling a function rather than asking for resourses through a url

For more detailed information about the JSON RPC specification, visit the official [JSON-RPC](http://www.jsonrpc.org/specification) website.

Below will be a comprehensive list of highlighted features of using JSON-RPC specification.

## Communication over HTTP

JSON-RPC is not a tangible framework or tool of anykind; rather, it is a set of guidlines and specifications to follow to ensure consistency. One of the first notable differences with utlizing an RPC style architecture is the way the communication protcol is handled. For this API, we will be communication over HTTP exclusively (other protcols commonly used are websockets/socket connections). 

**_JSON RPC communication will exclusively be sent as a POST request, resolving to the same URL route, and all control of what method is being requested and details to be sent to the API are handled in the request body as a JSON object request_**

An example will be used to compare the same call in both a RESTful architecute and the JSON-RPC specification

### RESTful webservice call

`GET http://test.example.com/api/users`

<aside class="success">
{
	"success": true,
	"result": [
		{
			"id": "123456"
		},
		{
			"id": "9076482"
		}
	]
}
</aside>

### JSON-RPC 2.0 call

`POST http://test.example.com/rpc`

<aside class="notice">
POST request body: 
{
	"jsonrpc": 2.0,
	"id": "randomtext",
	"method": "users.fetchUsers"
}
</aside>

<aside class="success">
Response Body: 
{
	"jsonrpc": 2.0,
	"id": "randomtext",
	"result": [
		{
			"id": "123456"
		},
		{
			"id": "9076482"
		}
	]
}
</aside>

What we are witnessing here is that a RESTful api call is heavily reliant on utilizing the different HTTP Verbs (GET, POST, PUT, DELETE, etc) in order to determine which resource driven method to route to since the same route, <domain>/api/users, can be used with different verbs to alter functionality. The same URL with the `POST` HTTP Verb would route to a entirely different method that would want to accept parameters and create or update a record saved in a database. 

The JSON RPC request contaisn the field `method` which leterally resolves to a method name on the server to call. RPC, (Remote Procedure Call), in the name describes this very idea. If we wanted to now make a call to get a specific user the calls would take different approaches:

### RESTful webservice call

`GET http://test.example.com/api/users/123456`

<aside class="success">
{
	"success": true,
	"result": {
		"id": "123456"
	}
}
</aside>

### JSON-RPC 2.0 call

`POST http://test.example.com/rpc`

<aside class="notice">
POST request body: 
{
	"jsonrpc": 2.0,
	"id": "randomtext",
	"method": "users.fetchUser"
	"params": {
		"userId": "123456"
	}
}
</aside>

<aside class="success">
Response Body: 
{
	"jsonrpc": 2.0,
	"id": "randomtext",
	"result": {
		"id": "123456"
	}
}
</aside>

The above example hows how the URL of a RESTful API gets modified in order to tell the API that we are now looking for a specific resource by appending the ID of the user resource after `/api/users/`. This architecture works well for most APIs, especially those where the content is read more often than it is updated since it oepns up the use for cacheing schems where the URL will be used to map a cached response. 

In a game such as this, where data has a potential of being updated quite rapidly, we don't have the same opportunity to utilize the same kind of cacheing schemes. Additionally, a game usually has a potentaily of wanting to communicate with the server more often that other types of applications, so providing an API that can be interacted with as a remote class (accessing resources in a functional, method call-like, mannor) can be an attractive feature. 

**Utilizing JSON-RPC, we loose the ability to use cacheing schemes but gain a more consistent and easier to interface with API.**

## Request/Response Types

JSON-RPC differ from RESTful APIs in that the specification describes a very strict set of guidlines in how Request Bodies should be constructed and how information will be returned.

### JSON-RPC Request Body

```json
{
	"jsonrpc": "2.0",
	"id": "1234",
	"method": "users.fetchUser",
	"params": {
		"userId": "4321"
	}
}
```

```json-doc
{
	"jsonrpc": "2.0",
	"id": "1234",
	"method": "users.fetchUser",
	"params": {
		"userId": "4321"
	}
}
```

| Field | Type | Defualt | Description |
| ---- | ---- | ---- | ---- |
| jsonrpc | String | 2.0 | This field describes what version of the specification the client app is expecting to follow. This is an important field to pass as 2.0 since the earlier specification was much less descriptive and how parameters where passed was only though and Array and the position of the parameters within that Array was important. |
| id | String |  | This is an optional field, technically. Because RPC can be used over different transport methods, the specification provides an interesting way to provide the calling client a way to ignore a response. The `id` field separates the difference between a _request_ method and a _notification_ method. A _notification_ method in JSON-RPC describes the ability for the client application to "notify" the server to run a particular method but is not concerned with the result of the method being called. In most cases, the _request_ method will be used in which the Request Body **MUST** contain something other than defined in the `id` field to let the server know that this is not a notification and the client expectes an asnwer back |
| method | String |  | This field is where most of the changes will be across requests. This field describes what remote method to call on the server and directly resolves to a method name in the server-side code base (generally). |
| params | Array/Object |  | If the method call being made expects some arguments, this field is where we provide the arguments for the method. This field an technically accept either an "array" of arguments or a map/dictionary/object with key/value pairs for the API to consume. With JSON-RPC 2.0, the specification was expanded to accept the map of key/values to remove the importance of the order of arguments when the server would consume the arguments of a request, making the call more flexible to consume. The key/values to be passed in this field will differ with each request so it is important to read the docuemntation for the request body of each method call. |

### JSON-RPC Response Body (Success)

```json
{
	"jsonrpc": "2.0",
	"id": "1234",
	"result": {
		"id": "4321"
	}
}
```

```json-doc
{
	"jsonrpc": "2.0",
	"id": "1234",
	"result": {
		"id": "4321"
	}
}
```

| Field | Type | Defualt | Description |
| ---- | ---- | ---- | ---- |
| jsonrpc | String | 2.0 | This field describes what version of the specification the client app is expecting to follow. |
| id | String |  | This will match the same id provided in the originating request body. This is mostly useful in the socket protocols as many of the messages will flow through the same socket listener so matching the ID would help the application determine what part of the app is looking for this response. |
| result | Array/Object |  | This field will contain the raw JSON array or JSON object that is the response from the method call made. |

### JSON-RPC Response Body (Error)

```json
{
	"jsonrpc": "2.0",
	"id": "1234",
	"error": {
		"code": 400,
		"message": "User does not exist",
		"data": "string or an object (determined by API)"
	}
}
```

```json-doc
{
	"jsonrpc": "2.0",
	"id": "1234",
	"error": {
		"code": 400,
		"message": "User does not exist",
		"data": "string or an object (determined by API)"
	}
}
```

| Field | Type | Defualt | Description |
| ---- | ---- | ---- | ---- |
| jsonrpc | String | 2.0 | This field describes what version of the specification the client app is expecting to follow. |
| id | String |  | This will match the same id provided in the originating request body. This is mostly useful in the socket protocols as many of the messages will flow through the same socket listener so matching the ID would help the application determine what part of the app is looking for this response. |
| error | Object |  | This field is going to contain detailed information about the reason for error. **code**: This field will contain a number indicating the error type that occurred. **message**: This field will contain a concise reason for failure. **data**: this field will contain detailed information about the reason for error |

## Batching

> Batched Request Body

```json
[
  {
	"jsonrpc": "2.0",
	"id": "1",
	"method": "users.fetchUsers"
  },
  {
	"jsonrpc": "2.0",
	"id": "2",
	"method": "users.fetchUser",
	"params": {
	  "userId": "4321"
	}
  }
]
```

```json-doc
[
  {
	"jsonrpc": "2.0",
	"id": "1",
	"method": "users.fetchUsers"
  },
  {
	"jsonrpc": "2.0",
	"id": "2",
	"method": "users.fetchUser",
	"params": {
	  "userId": "4321"
	}
  }
]
```

> Batched Response Body

```json
[
  {
    "jsonrpc": "2.0",
    "id": "1",
    "result": [
      {
        "id": "4321"
      },
      {
        "id": "98765"
      }
    ]
  },
  {
  	"jsonrpc": "2.0",
    "id": "2",
    "result": {
    	"id": "4321"
  	}
  }
]
```

```json-doc
[
  {
    "jsonrpc": "2.0",
    "id": "1",
    "result": [
      {
        "id": "4321"
      },
      {
        "id": "98765"
      }
    ]
  },
  {
  	"jsonrpc": "2.0",
    "id": "2",
    "result": {
    	"id": "4321"
  	}
  }
]
```

Ever wanted to be able to tell the server to do multiple things for you in a single network call? Welcome to JSON-RPC! Using this specification, it is a sinche to send a single request to batch multiple requests and get back a response for each one. 

<aside class="notice"> This is where we will see a significance for the "id" field </aside>

What we are witnessing here is that the request body has been changed from a JSON Object to a JSON Array containing multiple JSON-RPC Request bodies. Within the request, take note of the ids that were passed for each request in the array. When the server retuned with a response, the resul was an array of JSON-RPC Response Bodies with each result coresponding to their respective request ids. 