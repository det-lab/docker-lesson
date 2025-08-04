# Installing SSH Inside a Container
## Why Install SSH in a Container?
The main goal of installing SSH in a container here is for you to explore using SSH in conjunction with [this SSH tutorial at HSF.](https://hsf-training.github.io/hsf-training-ssh-webpage/)

In most cases, SSH is not necessary in containers. Docker is designed to run a single application per container, and you typically interact with it using `docker exec`, `docker attach` or Docker Compose. Adding SSH when you do not need it will increase the image size and can create potential security concerns depending on your use of the container. The Docker container in this exercise is custom made for this exercise which is why it has SSH in it - don't use it for the template in your Docker containers or you will unnecessarily include SSH.

## Step-by-step: Installing SSH in a Container
While using an Ubuntu terminal, we'll create an Ubuntu-based container, install OpenSSH Server, and configure it to accept connections. 

> For more information on using SSH, visit our HSF training page, [here](https://hsf-training.github.io/hsf-training-ssh-webpage/).
### 0. Open your terminal
If you're unsure how to open your terminal, refer to [the shell lesson on Software Carpentry.](https://swcarpentry.github.io/shell-novice/) On Windows, the appropriate application is often called Ubuntu. You can install a Terminal application from the Microsoft App Store for free. On a Mac, the appropriate application is called Terminal. On Linux, there are several different Terminal applications, and you may need to search 'terminal application + <your specific distribution>' to find the name.
### 1. Create a project folder (optional but recommended)
In the terminal, navigate to an appropriate directory that can house your project folder. For Mac and Linux users, the terminal starts in your home directory which is a reasonable place to work from. In Windows we recommend you to work in your Documents directory. This command will look like:
```bash
cd /mnt/c/Users/<your username>/Documents/
```
Then you can make a new folder and move into it using:
```bash
mkdir example-ssh-container
cd example-ssh-container
```
>NOTE: If you try to create a directory with an existing name, you'll run into the error:
```bash
mkdir: cannot create directory ‘example-ssh-container’: File exists
```
### 2. Create a file named `Dockerfile` (no file extension)
```bash
touch Dockerfile
```
### 3. Open the Dockerfile in a text editor
You can open the Dockerfile outside of WSL by navigating to it using finder (Mac) or the file explorer (Windows). Then you can right (or command) click on the file to open it with a text editor such as TextEdit (Mac) or Notepad (Windows).
### 4. Paste the Dockerfile content:
Please remember to read through this after pasting it and change your password.
```python
FROM ubuntu:22.04

# Install SSH Server
RUN apt-get update && apt-get install -y openssh-server

# Create SSH directory and set password for root - REPLACE PART IN ANGLE BRACKETS
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
docker build -t example-ssh-container .
```
* `-t` tags your image with a human-readable name.

* `.` tells Docker to look in the current directory for the Dockerfile.

This step may take a couple of minutes for your machine to complete.
### 7. Run a Container from the Image
```bash
docker run -d -p 2222:22 --name ssh-container example-ssh-container
```
* This maps port `22` inside the container to port `2222` on your machine.

You'll need to open a new terminal, on which you can now SSH in using:
```bash
ssh root@localhost -p 2222
```
This will prompt you to enter the password which was set in step 4 (`RUN mkdir /var/run/sshd && echo 'root:<your-new-password>' | chpasswd`). 

Now, you can refer to the [SSH tutorial](https://hsf-training.github.io/hsf-training-ssh-webpage/) and explore, even if you don't have an account on a cluster.

---

If you want to learn more about basic Docker commands, see [the next section](04_basic-commands.md). 