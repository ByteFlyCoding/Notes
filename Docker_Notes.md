---
title: "Docker_Notes"
date: 2021-03-31T19:45:02+08:00
draft: false
tags: ["Container", "Docker", "Cloud"]
categories: ["Kubernetes and Docker"]
---

# Docker_Notes

## Install Docker Engine on Ubuntu(Best Practice)

[Install Reference](https://docs.docker.com/engine/install/)

### Prerequisites

#### OS requirements

To install Docker Engine, you need the 64-bit version of one of these Ubuntu versions:

- Ubuntu Groovy 20.10
- Ubuntu Focal 20.04 (LTS)
- Ubuntu Bionic 18.04 (LTS)
- Ubuntu Xenial 16.04 (LTS)

Docker Engine is supported on `x86_64` (or `amd64`), `armhf`, and `arm64` architectures.

#### Uninstall old versions

```bash
sudo apt remove docker docker-engine docker.io containerd runc
```

It’s OK if apt-get reports that none of these packages are installed.

### Installation methods: Install using the repository

#### SET UP THE REPOSITORY

1. Update the apt package index and install packages to allow apt to use a repository over HTTPS:

   ```bash
   sudo apt update
   sudo apt install apt-transport-https ca-certificates curl gnupg lsb-release
   ```

2. Add Docker’s official GPG key:

   ```bash
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
   ```

3. Use the following command to set up the **stable** repository.

   ```bash
   echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   ```

#### INSTALL DOCKER ENGINE

1. Update the `apt` package index, and install the _latest version_ of Docker Engine and containerd：

   ```bash
   sudo apt update
   sudo apt install docker-ce docker-ce-cli containerd.io
   ```

2. Verify that Docker Engine is installed correctly by running the `hello-world` image.

   ```bash
   sudo docker run hello-world
   ```

## Uninstall Docker Engine

1. Uninstall the Docker Engine, CLI, and Containerd packages:

   ```bash
   sudo apt autoremove --purge docker-ce docker-ce-cli containerd.io
   ```

2. Images, containers, volumes, or customized configuration files on your host are not automatically removed. To delete all images, containers, and volumes:

   ```bash
   sudo rm -rf /var/lib/docker
   sudo rm -rf /var/lib/containerd
   ```
