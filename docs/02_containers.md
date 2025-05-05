# 2: Containers and Images
When working with Docker, two core concepts that you'll encounter are **container images** and **containers**. Understanding them both and the distinctions between them is key to the effective use of Docker.

## 2.1: Container Images
A **container image** can be likened to a packaged blueprint of a container, including everything that a program requires to run such as the code of the application itself, the required system libraries and dependencies, the configuration files and environment settings, etc.

Container images are **static** and **read-only** - you can think of them as snapshots or templates. Once built, they can be stored, shared, and reused on any system that supports Docker. 

Docker images are versioned and portable, allowing you to move seamlessly between development, testing, and production environments. 

## 2.2: Containers
Docker describes containers as "a standard unit of software" which packages all code and its dependencies. It can also be thought of as a **running instance** of a container image. When Docker starts a container, it creates a writable layer "on top" of the read-only image, before allowing the application to run in an isolated environment with its own file system, network interfaces, and process space. You can run multiple containers from the same image at the same time while allowing each container to act as an independent unit. 

For example, it might be useful to use the same database image to run one container for development, another for automated tests, and a third in production. Despite all coming from the same image, each container is able to store its own data and settings.

This separation between images (the blueprints) and containers (the running instances) allows Docker to quickly set up new environments, efficiently reuse resources, and ensure consistency across machines and stages of development.

## 2.3: Containers vs. Virtual Machines
While containers and virtual machines (VMs) might seem similar at a glance (both allow you to run isolated environments), the way that they achieve their isolation and their performance characteristics are significantly different. 

A virtual machine emulates an **entire computer**, including:
* Its own guest operating system.
* Virtual hardware, such as CPU, memory, disk, and network interfaces.
Each VM runs on top of a hypervisor, such as VirtualBox or VMware, which sits between the physical hardware and the virtual machine.

As mentioned before, a container **shares** the host's operating system kernal, simply isolating the file system, processes, and network. To summarize:

| Feature         | Virtual Machine                          | Container              |
|:----------------|-----------------------------------------:|-----------------------:|
| OS:             | Full OS per VM                           | Shares host OS kernel  |
| Startup Time:   | Minutes                                  | Seconds                |
| Resource Usage: | Heavy (GBs of disk space, RAM intensive) | Light (MBs to low GBs) |
| Isolation:      | Hardware-level                           | Process-level          |

---
Let's continue on to [section 3](03_installation.md) to install Docker and start working with containers.