# 4: Installing SSH Inside a Container
## Why Install SSH in a Container?
In most cases, SSH is not necessary in containers. Docker is designed to run a single applciation per container, and you typically interact with it using `docker exec`, `docker attach` or Docker Compose. Adding SSH can increase the image size, introduce complexity, and create potential security concerns.

However, there are situations in which installing SSH makes sense:

* **Legacy Systems:** You're containerizing an existing system that expects SSH access.

* **Remote Debugging:** You want to attach to containers from another machine using familiar SSH tools.

* **Custom VM-like Containers:** You're using containers in place of VMs and want them to behave similarly.

## Step-by-step: Installing SSH in a Container
While using an Ubuntu terminal, we'll create an Ubuntu-based container, install OpenSSH Server, and configure it to accept connections. 
> **Note:** Angled brackets in this lesson denote user-specific content - be sure to delete them and replace them to your preference.
> For more information on using SSH, visit our HSF training page, [here](https://hsf-training.github.io/hsf-training-ssh-webpage/).
### 1. Create a project folder (optional but recommended)
```bash
mkdir <your-ssh-container>
cd <your-ssh-container>
```
### 2. Create a file named `Dockerfile` (no file extension) using the Ubuntu terminal (WSL)
```bash
touch Dockerfile
```
### 3. Open the Dockerfile in a text editor:
* If you're using VS Code:
```Dockerfile
code Dockerfile
```
* Or use nano/vim:
```bash
nano Dockerfile
```
### 4. Paste the Dockerfile content:
```python
FROM ubuntu:22.04

# Install SSH Server
RUN apt-get update && apt-get install -y openssh-server

# Create SSH directory and set password for root - replace part in angle brackets
RUN mkdir /var/run/sshd && echo 'root:<your-new-password>' | chpasswd

# Allow root login (not recommended for production)
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# Expose port 22 and start SSH
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
```
### 5. Save and close the file.
### 6. Build the Image
In the same directory as your `Dockerfile`, run:
```bash
docker build -t <your-ssh-container> .
```
* `-t` tags your image with a human-readable name.

* `.` tells Docker to look in the current directory for the Dockerfile.

This step may take a couple of minutes for your machine to complete.
### 7. Run a Container from the Image
```bash
docker run -d -p 2222:22 --name ssh-container <your-ssh-container>
```
* This maps port `22` inside the container to port `2222` on your machine.
You should now be able to SSH in using:
```bash
ssh root@localhost -p 2222
```
This will prompt you to enter the password which was set in step 4 (`RUN mkdir /var/run/sshd && echo 'root:<your-new-password>' | chpasswd`). 

---

Let's continue now to [section 5](05_basic-commands.md) to learn some basic commands in Docker.