
# Docker and Kubernetes Commands

## Table of Contents
1. [Docker Basics](#docker-basics)
2. [Research Studies](#research-studies)
3. [USB and Ethernet Camera Connections](#usb-and-ethernet-camera-connections)
4. [Kubernetes Commands](#kubernetes-commands)

---

## Docker Basics

### General Info

#### List all running containers
```bash
docker container ls
```
Lists all the currently running containers, showing details like container IDs, names, and statuses.

#### Stop a container
```bash
docker container kill CONTAINER
```
Forcefully stops a running container by specifying its name or ID.

#### Remove a container
```bash
docker container rm CONTAINER
```
Deletes a stopped container permanently.

#### Inspect a container
```bash
docker inspect CONTAINER
```
Provides detailed configuration and status information about a container.

### Managing Images

#### List all locally available images
```bash
docker image ls
```
Displays all Docker images stored locally.

#### Remove an image
```bash
docker image rm IMAGE
```
Deletes a specific image from the local system.

#### Remove dangling images
```bash
docker image prune
```
Removes unused images that are not associated with any container.

#### Remove all images
```bash
docker image prune -a
```
Deletes all unused images from the system.

#### Tag an image
```bash
docker image tag IMAGE NEW_IMAGE
```
Tags an image with a new name or tag for easier reference or pushing to a repository.

#### Push an image to Docker Hub
```bash
docker tag IMAGE_ID yourhubusername/imagename:tag
docker push yourhubusername/imagename:tag
```
Tags and pushes an image to your Docker Hub repository.

---

## Research Studies

#### Build a Docker image
```bash
docker build -t python_rotate_img .
```
Builds a Docker image named `python_rotate_img` from the current directory.

#### Run a created Docker image
```bash
docker run -i -t python_rotate_img
```
Runs the previously created Docker image in an interactive terminal.

#### Run a Docker image with a specific port
```bash
docker run -p 8000:8000 python-fastapi
```
Runs the Docker image with port `8000` mapped to the host.

#### Copy a file from a running container
```bash
docker cp python-imutils-rotate:gray.png /gray_copy_docker.jpeg
```
Copies a file from a container to the local system.

#### Access a container with an interactive shell
```bash
docker exec -it CONTAINER_ID /bin/bash
```
Accesses the shell of a running container interactively.

#### Run a GPU-enabled Docker container
```bash
docker run -it --rm --gpus=all patchcore-main:latest /bin/bash
```
Runs a Docker container with GPU support enabled.

#### Check NVIDIA CUDA availability
```bash
docker run --rm --gpus all nvidia/cuda:11.0.3-base-ubuntu20.04 nvidia-smi
docker run --rm -it --gpus=all nvcr.io/nvidia/k8s/cuda-sample:nbody nbody -gpu -benchmark
```
Checks if NVIDIA CUDA libraries and drivers are accessible in the container.

#### Find a file within a container
```bash
sudo find / -name leather_glue_005.png
```
Searches for a specific file inside the container’s file system.

#### Run a container with XServer for GUI apps
```bash
docker run -it --rm --env="DISPLAY" --gpus=all -v /tmp/.X11-unix:/tmp/.X11-unix anomalib-wls:latest
```
Runs a Docker container with GUI applications visible on the host system using XServer.

---

## USB and Ethernet Camera Connections

#### USB Camera
```bash
sudo docker run -it --rm -v '/dev/bus/usb':'/dev/bus/usb' --privileged -e DISPLAY=$DISPLAY -v '/tmp/.X11-unix':'/tmp/.X11-unix' basler_usb:latest /bin/bash
```
Connects to a USB camera inside a container. The `--privileged` flag and volume mounting are necessary for device access.

#### Ethernet Camera
```bash
sudo docker run -it --rm --net host -e DISPLAY=$DISPLAY -v '/tmp/.X11-unix':'/tmp/.X11-unix' basler_usb:latest /bin/bash
```
Connects to an Ethernet camera using the host network configuration.

---

## Kubernetes Commands

#### Apply a deployment configuration
```bash
kubectl apply -f deployment.yaml
```
Deploys applications using the configurations specified in `deployment.yaml`.

#### Delete all pods
```bash
kubectl delete --all pods
```
Deletes all running pods in the current namespace.

#### Get all running pods
```bash
kubectl get pods
```
Lists all running pods and their statuses.

#### Delete all deployments
```bash
kubectl delete --all deployments
```
Deletes all active deployments in the current namespace.
