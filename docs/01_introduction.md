# 1: Introduction
Docker is a tool which allows users to build, share, package, verify, and run applications in isolated environments called **containers** while avoiding the tedium of environment confirguration and management.

It's not uncommon when programming collaboratively that something that might work well on one user's environment will run into issues when another user tries to run the same steps. Docker ensures that applications and their dependencies are bundled together in a portable format, side-stepping the classic "well, it works on my machine" issue which can be otherwise difficult to solve. Whether developing from your personal laptop or deploying to production servers, Docker helps to ensure that the environment stays consistent.

**Containers** are lightweight and fast, built to share the host's operating system's kernal rather than running full virtual machines. This makes them efficiently capable of isolating processses, testing software in clean environments, or managing complex multi-service applications without polluting your local system.

In this lesson, we'll explore:

* What containers are and how they differ from virtual machines.

* How to install Docker and run your first container.

* How to install SSH inside a container, and why you might choose to do so.

* How to use basic Docker commands to build, inspect, and manage your containers.

* Practical examples to illustrate how Docker can simplify both development and deployment workflows.


By the end of this lesson, you should have a working understanding of how to use Docker to create reliable and reproducible environments for your projects. 

---

Let's continue to [section 2](02_containers.md) to begin learning about container images and containers.