# holbertonschool-softy-pinko-docker

## Docker Overview

Docker is a platform that enables you to containerize your applications, packaging them into portable, self-contained environments that can run anywhere. This eliminates concerns about dependencies or configuration issues when moving applications between environments, such as from a local machine to a server. Docker uses containers—lightweight, isolated environments containing everything an application needs to run, including libraries, dependencies, and configurations. Containers can be started and stopped quickly, making them ideal for modern software development and deployment.

With Docker, you can scale applications efficiently by running multiple containers of the same application on different hosts (or the same host, as in this project). Tools like Docker Compose or other orchestration solutions can help manage these containers.

In this project, you will build an infrastructure for an application that includes:
- A reverse proxy
- A load balancer
- Two application servers
- One front-end server

---

## High-Level Design

The design features a single server acting as the entry point for your application. This server functions as:
1. A **reverse proxy** to route traffic to either the API servers or the front-end static-content server.
2. A **load balancer** to distribute traffic between the two API servers.

### Traffic Flow:
- **Front-End Requests**: If a request is routed to the front-end static-content server, the server processes it and sends the response back to the proxy server, which then forwards it to the client. The client does not directly communicate with the front-end server.
- **API Requests**: If a request is routed to the API server, the load balancer uses a Round Robin algorithm to determine which API server will handle the request. The response is sent back to the proxy server, which forwards it to the client. The client does not directly communicate with the API servers.

---

### What is Round Robin Load Balancing?

Round Robin load balancing distributes traffic across multiple servers in a rotating manner. For example, with three servers (A, B, and C):
1. The first request goes to server A.
2. The second request goes to server B.
3. The third request goes to server C.
4. The fourth request cycles back to server A, and so on.

This ensures an even distribution of traffic, preventing any single server from being overwhelmed. While simple and effective, Round Robin may not suit applications with varying workload patterns or resource requirements. However, it is sufficient for the purposes of this project.

---

## Prerequisites

Before starting, ensure the following:
1. **Install Docker Desktop** on your local machine (not your sandbox).  
    [Download Docker Desktop](https://www.docker.com/)  
    For detailed installation instructions, refer to:
    - [Windows Installation Guide](https://docs.docker.com/desktop/install/windows-install/)
    - [Mac Installation Guide](https://docs.docker.com/desktop/install/mac-install/)
    - [Linux Installation Guide](https://docs.docker.com/desktop/install/linux-install/)
    - **Note for Chromebook Users**: You can install the Docker engine, but not Docker Desktop. Consider using a Windows, Mac, Linux machine, or a campus machine instead.

2. **Familiarize Yourself with Docker**  
    - [Docker Tutorial](https://docs.docker.com/get-started/)

---

## Useful Resources

- [Docker Cheatsheet](https://dockerlabs.collabnix.com/docker/cheatsheet/)
- [Proxy vs Reverse Proxy (Real-world Examples)](https://www.nginx.com/resources/glossary/reverse-proxy-vs-proxy-server/)
- [What is a Reverse Proxy? (vs. Forward Proxy)](https://www.youtube.com/watch?v=TeU6pHcpkKA) *(Stop at 06:25)*
