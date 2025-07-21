# 5: Basic Docker Commands
Once Docker is installed, you'll primarily use the `docker` CLI to interact with images and containers. Here's some of the essential commands that cover the full lifecycle: build, run, inspect, and manage.
## Building a Docker Image
To create a container, you first need an image. If you have a `Dockerfile`, you can build an image from it:
```bash
docker build -t <your-image-name> .
```
As mentioned in the previous section, the command `-t` tags your image with a human-readable name, while `.` specifies the current directory as the build context.

Also - for help writing your Dockerfile, reference the official documentation for commands [here](https://docs.docker.com/reference/dockerfile/).
## Running a container
To create and start a container from an image, run:
```bash
docker run -it --name <your-container> <your-image-name>
```
* `-it`: Attaches an interactive terminal.

* `--name <your-container>`: Assigns a name to the container.

* `<your-image-name>`: Refers to the image built earlier.

To run container in the background:
```bash
docker run -d --name <your-container> <my-image-name>
```
To map a port from your host machine to the container, such as host port 8080 to container port 80:
```bash
docker run -d -p 8080:80 <your-image-name>
```
## Inspecting Containers
* List running containers:
```bash
docker ps
```
* List all containers, including stopped ones:
```bash
docker ps -a
```
* View container logs:
```bash
docker logs <your-container>
```
* Inspect low-level configuration and state:
```bash
docker inspect <your-container>
```
* Check real-time resource usage, such as CPU and memory:
```bash
docker stats
```
## Managing Containers:
* Stop a running container:
```bash
docker stop <your-container>
```
* Start a stopped container:
```bash
docker start <your-container>
```
* Restart a container:
```bash
docker restart <your-container>
```
* Remove a stopped container:
```bash
docker rm <your-container>
```
* Remove an image:
```bash
docker rmi <your-image-name>
```
## Cleanup Tips
* Remove all stopped containers:
```bash
docker container prune
```
* Remove unused images:
```bash
docker image prune
```
* Remove all unused containers, networks, and images:
```bash
docker system prune
```

---

Now that you know how to build, run, and manage containers, we can continue to [section 6](06_examples.md) to show how Docker can simplify development and deployment workflows.