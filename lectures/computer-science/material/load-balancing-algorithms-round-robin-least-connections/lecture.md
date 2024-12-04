# Load Balancing Algorithms: Round Robin, Least Connections

## Round Robin

Round Robin is a simple method for distributing client requests across a group of servers. When a request comes in, it is forwarded to the next server in the list. Once it reaches the end of the list, it starts again from the top.

Here's a pseudo-code example of how this could be implemented:

```python
servers = ['server1', 'server2', 'server3']
current_index = 0

def handle_request(request):
    global current_index
    server = servers[current_index]
    forward_request_to(server, request)
    current_index = (current_index + 1) % len(servers)
```

This approach is easy to implement but doesn't consider the load of each server.

## Least Connections

The Least Connections method goes a step further by keeping track of the number of open connections for each server. The idea is to try to equalize the amount of work each server is doing at any given moment. When a request comes in, the balancer forwards it to the server currently handling the fewest connections.

Here's a pseudo-code implementation of this algorithm:

```python
servers = {'server1': 0, 'server2': 0, 'server3': 0}

def handle_request(request):
    # Find the server with the least connections
    server = min(servers, key=servers.get)
    forward_request_to(server, request)
    servers[server] += 1

def close_connection(server):
    servers[server] -= 1
```

In this scenario, the `handle_request` function picks the server with the fewest connections, and `close_connection` is called when a request is finished, decreasing the count.

Both algorithms have their uses. Round Robin is simple and effective in many situations, while Least Connections is more sophisticated and can yield better results when the servers have differing capabilities or loads.
