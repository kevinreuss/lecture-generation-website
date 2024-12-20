# Socket Programming Basics

Socket Programming is a method of communication between two computers using a network protocol, typically TCP/IP.

## What is a Socket?

In the context of networking, a socket is an endpoint in a communication flow between two systems. You can think of it as the door leading into your house, but in a networked environment. It's identified by an IP address and a port number.

## Types of Sockets

There are two main types of sockets used in programming:

- **Stream Sockets** (SOCK_STREAM): They use TCP (Transmission Control Protocol) for data transmission. They are reliable because they guarantee delivery of packets in the same order they were sent.

- **Datagram Sockets** (SOCK_DGRAM): They use UDP (User Datagram Protocol). They are unreliable, packets might be lost or arrive out of order.

## Python Socket Programming

Python provides a `socket` module that simplifies socket programming. Here's a basic example of creating a TCP/IP socket:

```python
import socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
```

In this code, `AF_INET` is the address family for IPv4 and `SOCK_STREAM` specifies that this is a TCP socket.

## Establishing a Connection

A server program listens for connections on a specific IP address and port. A client program can then connect to the server.

Here's a basic example of a server listening for connections:

```python
import socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind(("localhost", 12345))
s.listen(1)
conn, addr = s.accept()
```

In this code, `bind(("localhost", 12345))` specifies the IP and port to listen on. `listen(1)` means that the socket can queue up to 1 client connection. `accept()` blocks and waits for an incoming connection; when a client connects, it returns a new socket object representing the connection and the address of the client.

A client can connect to the server like this:

```python
import socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(("localhost", 12345))
```

`connect(("localhost", 12345))` is used to connect to the server listening on the specified IP and port.

## Sending and Receiving Data

Data is sent and received in bytes. Here's how a server can send data:

```python
conn.sendall(b'Hello, client')
```
And this is how a client can receive data:

```python
data = s.recv(1024)
```

In these examples, `sendall(bytes)` sends data from the server to the client, and `recv(bufsize)` receives data from the server at the client side. Here `bufsize` is the maximum amount of data to be received at once.