### Docker overview
Docker is an open platform for developing, shipping, and running applications. Docker enables you to separate your applications from your infrastructure so you can deliver software quickly. 
With Docker, you can manage your infrastructure in the same ways you manage your applications. 
By taking advantage of Docker's methodologies for shipping, testing, and deploying code, you can significantly reduce the delay between writing code and running it in production.

#### The Docker platform
Docker provides the ability to package and run an application in a loosely isolated environment called a container. 
The isolation and security lets you to run many containers simultaneously on a given host. 
Containers are lightweight and contain everything needed to run the application, so you don't need to rely on what's installed on the host.
You can share containers while you work, and be sure that everyone you share with gets the same container that works in the same way.

#### Docker provides tooling and a platform to manage the lifecycle of your containers:
- Develop your application and its supporting components using containers.
- The container becomes the unit for distributing and testing your application.
- When you're ready, deploy your application into your production environment, as a container or an orchestrated service. 
This works the same whether your production environment is a local data center, a cloud provider, or a hybrid of the two.

#### Responsive deployment and scaling
Docker's container-based platform allows for highly portable workloads. 
Docker containers can run on a developer's local laptop, on physical or virtual machines in a data center, on cloud providers, or in a mixture of environments.

Docker's portability and lightweight nature also make it easy to dynamically manage workloads, scaling up or tearing down applications and services as business needs dictate, in near real time.

#### Running more workloads on the same hardware
Docker is lightweight and fast. It provides a viable, cost-effective alternative to hypervisor-based virtual machines, so you can use more of your server capacity to achieve your business goals. 
Docker is perfect for high density environments and for small and medium deployments where you need to do more with fewer resources.

### Docker architecture
Docker uses a client-server architecture. The Docker client talks to the Docker daemon, which does the heavy lifting of building, running, and distributing your Docker containers. 
The Docker client and daemon can run on the same system, or you can connect a Docker client to a remote Docker daemon. 
The Docker client and daemon communicate using a REST API, over UNIX sockets or a network interface. 
Another Docker client is Docker Compose, that lets you work with applications consisting of a set of containers.

![image](https://github.com/K4ME/devops-notebook/assets/33429566/db494e3e-6311-4489-863c-b3769009e66e)

#### The Docker daemon
The Docker daemon (dockerd) listens for Docker API requests and manages Docker objects such as images, containers, networks, and volumes. 
A daemon can also communicate with other daemons to manage Docker services.

#### The Docker client
The Docker client (docker) is the primary way that many Docker users interact with Docker. When you use commands such as docker run, the client sends these commands to dockerd, which carries them out. 
The docker command uses the Docker API. The Docker client can communicate with more than one daemon.

#### Docker Desktop
Docker Desktop is an easy-to-install application for your Mac, Windows or Linux environment that enables you to build and share containerized applications and microservices. 
Docker Desktop includes the Docker daemon (dockerd), the Docker client (docker), Docker Compose, Docker Content Trust, Kubernetes, and Credential Helper. For more information, see Docker Desktop.

#### Docker registries
A Docker registry stores Docker images. Docker Hub is a public registry that anyone can use, and Docker looks for images on Docker Hub by default. You can even run your own private registry.

When you use the docker pull or docker run commands, Docker pulls the required images from your configured registry. When you use the docker push command, Docker pushes your image to your configured registry.


### Docker objects
When you use Docker, you are creating and using images, containers, networks, volumes, plugins, and other objects. 

#### Images
An image is a read-only template with instructions for creating a Docker container. Often, an image is based on another image, with some additional customization. 
For example, you may build an image which is based on the ubuntu image, but installs the Apache web server and your application, as well as the configuration details needed to make your application run.

You might create your own images or you might only use those created by others and published in a registry. 
To build your own image, you create a Dockerfile with a simple syntax for defining the steps needed to create the image and run it. 
Each instruction in a Dockerfile creates a layer in the image. When you change the Dockerfile and rebuild the image, only those layers which have changed are rebuilt. 
This is part of what makes images so lightweight, small, and fast, when compared to other virtualization technologies.

#### Containers
A container is a runnable instance of an image. You can create, start, stop, move, or delete a container using the Docker API or CLI. 
You can connect a container to one or more networks, attach storage to it, or even create a new image based on its current state.

By default, a container is relatively well isolated from other containers and its host machine. 
You can control how isolated a container's network, storage, or other underlying subsystems are from other containers or from the host machine.

A container is defined by its image as well as any configuration options you provide to it when you create or start it. 
**When a container is removed, any changes to its state that aren't stored in persistent storage disappear.**


[Source](https://docs.docker.com/get-started/overview/)
