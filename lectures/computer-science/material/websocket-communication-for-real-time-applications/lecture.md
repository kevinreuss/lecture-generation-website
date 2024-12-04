# WebSocket Communication for Real-Time Applications

WebSocket is a protocol that provides full-duplex communication channels over a single TCP connection. It is designed to be implemented in browsers and web servers but can be used by any client or server application.

In contrast with HTTP, WebSocket provides real-time bidirectional communication. Once a WebSocket connection is established, it stays open until the client or server decides to close this connection.

## Creating a WebSocket Connection

In JavaScript, WebSocket connection can be created using the `WebSocket` constructor. Here's an example:

```javascript
const socket = new WebSocket('ws://localhost:8080');
```

The URL scheme to be used is "ws". The connection is established by upgrading an existing HTTP connection.

## Receiving Messages from the Server

Once the connection is open, you can then register event listeners to receive messages from the server:

```javascript
socket.onmessage = function(event) {
  console.log("Received: " + event.data);
};
```

## Sending Messages to the Server

To send data to the server, use the `send()` method:

```javascript
socket.send("Hello Server!");
```

## Closing the Connection

The connection can be closed by invoking the `close()` method:

```javascript
socket.close();
```

## Handling Connection Errors

To handle potential errors, use the `onerror` event handler:

```javascript
socket.onerror = function(error) {
  console.log("WebSocket Error: ", error);
};
```

## WebSocket Server

On the server side, you can use libraries like `ws` on Node.js to create a WebSocket server. Here's a simple server that echoes back the messages it receives:

```javascript
const WebSocket = require('ws');

const wss = new WebSocket.Server({ port: 8080 });

wss.on('connection', (ws) => {
  ws.on('message', (message) => {
    console.log('received: %s', message);
    ws.send(`Hello, you sent -> ${message}`);
  });
});
```

In a nutshell, WebSocket provides a much more efficient communication method for real-time applications compared to traditional HTTP requests, enabling you to create highly interactive applications with ease.