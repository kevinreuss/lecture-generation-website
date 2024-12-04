# Docker Containers and Orchestration

## Docker Containers

Docker containers are lightweight, standalone, executable packages that include everything needed to run a piece of software. They wrap software in a complete filesystem that contains code, runtime, system tools, and libraries, ensuring that the software runs consistently on any infrastructure.

Here's an example of a Dockerfile, which describes an image:

```Dockerfile
FROM python:3.7-alpine
WORKDIR /app
COPY . /app
RUN pip install -r requirements.txt
CMD ["python", "app.py"]
```

This Dockerfile takes a Python 3.7 base image, sets the working directory to `/app`, copies the current directory into `/app`, installs the Python dependencies, and sets the default command to run the application.

## Docker Orchestration

Orchestration in the context of Docker involves managing the lifecycles of containers, especially in large, dynamic environments. Docker Swarm and Kubernetes are popular tools for Docker orchestration.

### Docker Swarm

Swarm is Docker's built-in orchestration tool. It uses the standard Docker API, making it compatible with any tool that already works with Docker daemon.

Here's an example of creating a Docker Swarm:

```bash
$ docker swarm init --advertise-addr <MANAGER-IP>
$ docker swarm join --token <TOKEN> <MANAGER-IP>:2377
```

The first command initializes a new swarm, and the second command adds a new node to the swarm.

### Kubernetes

Kubernetes, on the other hand, is a more powerful orchestration tool, capable of handling more complex use-cases. It manages and scales applications composed of multiple containers, across multiple hosts.

Here's an example of a Kubernetes Deployment:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  selector:
    matchLabels:
      app: nginx
  replicas: 3
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```

This Deployment creates three replicated Pods, which are managed as a group.