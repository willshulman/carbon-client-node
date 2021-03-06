class RestClient
----------

A ```RestClient``` is a client object used for accessing RESTFul resources such as Endpoints and Collections.

Constructor
----------
#### RestClient(url, options)
**Parameters**
* ```url``` _string_: Url for RESTFul server. e.g. http://localhost:8888.

* ```options``` _object_ _(optional)_: An object for specifying client options. e.g. "authentication".

**options**
* ```authentication``` - An object for specifying authentication configuration for the client

```node
//API Key Authentication

authentication: {
  type: "api-key",
  apiKey: <string>,
  apiKeyParameterName: <string>,
  apiKeyLocation: "header" OR "query"
}
```
Methods
----------

#### getEndpoint(path)

**Parameters**
* ```path``` - relative path of endpoint

**Returns** (```Endpoint```): An ```Endpoint```.

#### getCollection(path)

**Parameters**
* ```path``` - relative path of collection

**Returns** (```Collection```): A ```Collection```.


Examples
----------

```node
// require the client
var RestClient = require('carbon-client-node')

// create the client object
var client = new RestClient("http://localhost:8888")

// request the /hello endpoint
client.getEndpoint("hello").get(function(e, res) {
  console.log("Response from /hello: " + res.body)
})

// request the /users collection
client.getCollection("users").get(function(e, data) {
  console.log("Users:")
  console.log(data)
})
```


```node
// authentication example

var client = new RestClient("http://localhost:8888", {
  authentication: {
    type: "api-key",
    apiKey:"123",
    apiKeyParameterName: "API_KEY",
    apiKeyLocation: "header"
  }
})

```

