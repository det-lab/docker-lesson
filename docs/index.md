# Introduction
In this lesson, we'll explore:

* What containers are and how they differ from virtual machines.

* How to install Docker and run your first container.

* How to install SSH inside a container, and why you might choose to do so.

* Use a Docker container to explore SSH

* How to use basic Docker commands to build, inspect, and manage your containers.

* Practical examples to illustrate how Docker can simplify both development and deployment workflows.

Docker is a tool which allows users to build, share, package, verify, and run applications in isolated environments called **containers** while avoiding the tedium of environment configuration and management.

It's not uncommon when programming collaboratively that something that works well on one user's environment will run into issues when another user tries to run the same steps. Docker solves this problem by having dependencies and environment settings bundled together in a portable format. Whether you're developing from your personal laptop, running code on a high performance computing cluster, or deploying to production servers, Docker helps to ensure that the environment stays consistent.

**Containers** are lightweight and fast, built to share the host's operating system's kernel rather than running full virtual machines. This makes them ideal for testing software in clean environments.

By the end of this lesson, you should have a working understanding of how to use an existing Docker file to run a service with SSH. If you want to continue to learn more about Docker after this lesson here are some additional resources:

* [The Carpentries Community Lessons.](https://carpentries.org/lesson-development/community-lessons/) Use the search box at the bottom to search "containers" to find more relevant lessons.

* [The HSF Training Center.](https://hsf-training.org/training-center/) Articles of interest to you may be the ones for Docker, Singularity, and Reproducible Analysis with REANA.

* [How Containers Work!](https://store.wizardzines.com/products/how-containers-work) by Julia Evans. If you really want to understand how containers work, this is the best resource available.

---

Let's continue to [the next section](01_installation.md) to begin learning about container images and containers.