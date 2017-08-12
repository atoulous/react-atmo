# React Atmo

React atmo is a custom renderer for [express](https://expressjs.com/).

## Getting Started

```
npm install --save react-atmo
```

## Hello, world!

```js
import React from "react";
import Atmo from "react-atmo";

Atmo.listen(
  <server port="9000">
    <route method="get" url="/user/capability">
      <response>
        {() => ({
          user: "Adlee",
          isAdmin: false
        })}
      </response>
      <headers>
        <header name="content-type" value="application/json" />
        <jsonContentType />
        <crossOrigin />
      </headers>
    </route>
  </server>
);
```

## API
### `Atmo.listen(element, [callback])`
Starts an electron app.

## Elements
### `<server>`
Creates a server app and starts listening on the provided port
* port - Port to start the server

### `<route>`
Attaches the route to the express app
* method - Http method name for the route. Supports all the methods those are supported by express.

* url - Url of the route.

### `<response>`
Represents the response of the route. Takes a function as a children. Whatever the function returns would be returned by the route.

Response function also receives request and response objects of express if you want to do something interesting.
```
<response>
  {(request, response) => {
    // play with the request and response object of express
    return {
      status: 'alive'
    }
  }}
</response>
```

### `<headers>`
Takes headers as children.

### `<header>`
Represents a response header

* name - Header name
  
* value - Header value
  
There are bunch of short hand headers for the commonly used headers as follows.

* jsonContentType - Adds JSON content type header
* xmlContentType - Adds XML content type header
* textContentType - Adds text content type header
* crossOrigin - Cross origin header

## Inspiration and Reference
[React-ionize](https://github.com/mhink/react-ionize) is a react custom renderer which targets electron. I have used react-ionize as a reference to build react-atmo. Infact I have used it as a boilerplate.