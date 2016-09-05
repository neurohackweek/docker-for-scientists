---
title: "Installing Docker"
teaching: 5
exercises: 10
questions:
- "How do I install Docker?"
objectives:
- "Install Docker on your laptop"
keypoints:
- "Docker runs on Windows, Mac OS X, and Linux."

- Decide between "Docker for.." and "docker-machine".

---

### Docker installation

Before we begin, we need to install Docker!

- [Windows](https://docs.docker.com/engine/installation/windows/)
- [Mac OS X](https://docs.docker.com/engine/installation/mac/)
- [Linux](https://docs.docker.com/engine/installation/linux/)

### What's `Docker Toolbox`? Do I need it?

If your OS does not meet the requirements of `Docker for Windows` or `Docker for Mac` you will need to install [VirtualBox](https://www.virtualbox.org) and [Docker Toolbox](https://www.docker.com/products/docker-toolbox).


### When it's finished
Before running containers you need to give Docker acces too you locla hard drives. This can be enabled in Settings->Shared Drives.
When your installation is completed open a terminal (console/cmd) and type:

`docker pull bids/base_fsl`
