# 5: Basic Docker Commands
Once Docker is installed, you'll primarily use the `docker` CLI (Command-Line Interface) to interact with images and containers. Here's some of the essential commands that cover the full lifecycle: build, run, inspect, and manage. You will need to run these commands in a shell.
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

If you want to continue to learn more about Docker after this lesson here are some additional resources:

* [The Carpentries Community Lessons.](https://carpentries.org/lesson-development/community-lessons/) Use the search box at the bottom to search "containers" to find more relevant lessons.

* [The HSF Training Center.](https://hsf-training.org/training-center/) Articles of interest to you may be the ones for Docker, Singularity, and Reproducible Analysis with REANA.

* [How Containers Work!](https://store.wizardzines.com/products/how-containers-work) by Julia Evans. If you really want to understand how containers work, this is the best resource available.