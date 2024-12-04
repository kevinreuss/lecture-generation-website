# Cross-Origin Resource Sharing (CORS)

Cross-Origin Resource Sharing (CORS) is a mechanism that allows restricted resources (e.g., fonts, JavaScript, etc.) on a web page to be requested from another domain outside the domain from which the resource originated.

## How CORS works

When a client makes a cross-origin request, it includes an `Origin` header. The server can respond with an `Access-Control-Allow-Origin` header to authorize the request. If the server does not respond with this header, or if the header does not match the origin of the client, the browser will block the request.

```javascript
// client-side code
fetch('https://example.com', {
  method: 'GET',
  headers: {
    'Origin': 'https://your-website.com'
  }
})
```

```http
// server-side response
HTTP/1.1 200 OK
Access-Control-Allow-Origin: https://your-website.com
```

## Pre-flight request

For certain types of requests, browsers will send a pre-flight request before the actual request. This is done using the `OPTIONS` method, and it allows the server to respond whether it will accept the actual request, based on the `Origin`, `Access-Control-Request-Method`, and `Access-Control-Request-Headers` headers.

```http
OPTIONS /resource HTTP/1.1
Origin: https://your-website.com
Access-Control-Request-Method: POST
Access-Control-Request-Headers: X-PINGOTHER, Content-Type
```

The server can respond with `Access-Control-Allow-Origin`, `Access-Control-Allow-Methods`, and `Access-Control-Allow-Headers` headers to indicate acceptance of the actual request.

```http
HTTP/1.1 204 No Content
Access-Control-Allow-Origin: https://your-website.com
Access-Control-Allow-Methods: POST, GET
Access-Control-Allow-Headers: X-PINGOTHER, Content-Type
```

## Handling CORS in server-side

In Node.js, for example, you can use the `cors` middleware package to handle CORS.

```javascript
const express = require('express');
const cors = require('cors');

const app = express();

app.use(cors({ origin: 'https://your-website.com' }));

app.get('/resource', (req, res) => {
  res.send('Hello, CORS!');
});

app.listen(3000);
```

In this example, the server will accept requests from `https://your-website.com` and send the appropriate `Access-Control-Allow-Origin` response header.
