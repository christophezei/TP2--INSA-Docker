# TP 2: Multi-Architecture Docker Compose Application

## Objective: 

Create a Docker Compose configuration for a multi-container application where one container is built for ARM architecture,
and another is built for x86 architecture. These containers will communicate with each other.

## Requirements:

- Basic understanding of Docker concepts.
- Docker installed on the localmachine.
- Qemu installed for arm emulation on your x86 machine.
- A text editor for creating Docker Compose files (e.g., VSCode,
Sublime Text, etc.).

## Instructions:


## Install QEMU: 

To build the ARM image on an x86 machine, use QEMU for emulation. 
Install and test QEMU by running the following commands:
   
   ```  
   sudo apt-get install qemu binfmt-support qemu-user-static
   docker run --rm --privileged multiarch/qemu-user-static --reset -p yes
   docker run --rm -t arm64v8/ubuntu uname -m # Testing the emulation environment

   ```
Now the qemu-arm-static binary is under /usr/bin on your localmachine.
## Create Dockerfiles: 

Create two Dockerfiles: 

- One for ARM (Dockerfile.arm)
- Another for x86 (Dockerfile.x86).
- Use Ubuntu images for x86 and arm:
  
   ```
   ubuntu:latest
   arm64v8/ubuntu:latest
   ```
In each Dockerfile, create a simple script (e.g., a "Hello World" program) that prints the architecture it is running on.

## Create Docker Compose File 

- Create a docker-compose.yml file in the same directory.
- Define two services: one for ARM and another for x86.
- Specify the build context and Dockerfile for each service.

## Configure Services:

- Set up a Docker network.
- Ensure that the services can communicate with each other by using the ping command from each "script.sh".

## Build and Run: 

- Use docker compose up to build and run the multi-container application.
- Verify that each service correctly prints the architecture it is running on.

## Volume Configuration :

Volumes in Docker allow you to persist data between container runs and share files between the container and your local machine. This can be useful for saving logs, databases, or any other data your application generates.

- Extend the Docker Compose file to define volumes for both ARM and x86 services.
- Mount these volumes to directories on your local machine.
- Update the Dockerfiles or scripts to write files within the mounted volumes. For example, modify your scripts to perform a simple echo operation that saves a .txt file

## Cleanup: 

Use docker compose down to stop and remove the containers.

## Conclusion:

Congratulations! By completing this exercise, you have acquired essential skills in building a multi-architecture Docker Compose application. Throughout this journey, you have learned to create Dockerfiles optimized for ARM and x86 architectures, ensuring compatibility across diverse platforms. The integration of QEMU for ARM emulation on x86 machines has equipped you with a valuable technique for cross-architecture development. Additionally, you have explored the significance of Docker volumes, mastering the art of data persistence and file sharing between containers and your local machine. By successfully configuring services, enabling communication, and managing volumes, you have developed practical insights into orchestrating multi-container applications with Docker Compose. This exercise encourages collaboration and hands-on experimentation, providing you with valuable experience in deploying and maintaining multi-architecture containerized environments.

