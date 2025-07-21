# Initial Requirments
This lesson will assume a working understanding of how to use the Unix Shell. If you are new to the Unix shell, we recommend first doing the [Software Carpentry Unix Shell tutorial](https://swcarpentry.github.io/shell-novice/). Another tutorial that might be useful is my [Unix Introduction lesson](https://det-lab.github.io/unix-tips/).
# Installing Docker
Docker Desktop is the primary application for managing containers on your local machine. It provides a user-friendly GUI, integrates with your system's Command-Line Interface (CLI) tools, and includes everything necessary to build and share containerized apps. 

Docker is completely free for personal use. You can begin your download by following [this link to the official site](https://www.docker.com/products/docker-desktop/). Docker has download options for Mac (Apple Silicon or Intel Chip), Windows (AMD64 or ARM64), and Linux. You may be prompted to enable WSL2 (on Windows), grant system permissions (on macOS), or install supporting packages (on Linux). The installer will walk you through these steps automatically. This installation will also require you to restart your machine to be completed, so be sure to save important work before doing this installation.

After completing your installation, open a terminal (or command prompt for Windows) and run:
```bash
docker run hello-world
```
This will download the `hello-world` image if it's not already present before running a small container which prints a confirmation message if everything is working correctly. Running this helps to verify that your Docker Engine is running correctly and that Docker can fetch and execute containers from Docker Hub. If this works, your installation is complete and functional. If it fails to run, make sure that Docker Desktop is open and running. On some systems, you may need to enable virtualization in your BIOS or allow Docker through your firewall.

---

Let's continue to [the next section](02_containers.md) to learn about the basics of containers.