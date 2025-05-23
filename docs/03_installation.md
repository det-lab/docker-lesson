# 3: Installing Docker
Docker Desktop is the primary application for managing containers on your local machine. It provides a user-friendly GUI, integrates with your system's Command-Line Interface (CLI) tools, and includes everything necessary to build and share containerized apps. 
While there are several paid options for using Docker, it is completely free for personal use. If you are planning on using Docker for advanced and professional use, [click here](https://www.docker.com/pricing/) to see the pricing options. Otherwise, you can begin your download by following [this link to the official site](https://www.docker.com/products/docker-desktop/). Docker has download options for Mac (Apple Silicon or Intel Chip), Windows (AMD64 or ARM64), and Linux. You may be prompted to enable WSL2 (on Windows), grant system permissions (on macOS), or install supporting packages (on Linux). The installer will walk you through these steps automatically. This installation will also require you to restart your machine to be completed, so be sure to save important work before doing this installation.

After completing your installation, open a terminal (or command prompt for Windows) and run:
```bash
docker run hello-world
```
This will download the `hello-world` image if it's not already present before running a small container which prints a confirmation message if everything is working correctly. Running this helps to verify that your Docker Engine is running correctly and that Docker can fetch and execute containers from Docker Hub. If this works, your installation is complete and functional. If it fails to run, make sure that Docker Desktop is open and running. On some systems, you may need to enable virtualization in your BIOS or allow Docker through your firewall.

---

Let's continue to [section 4](04_docker-ssh.md) to learn how to set up an SSH inside a container.