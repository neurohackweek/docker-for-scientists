---
title: "Pulling and running a container"
teaching: 10
exercises: 0
questions:
objectives:
- "Pull (download) an image from Docker Hub"
- "Run shell inside a container"
- "Mount local folders"
- "Apply software from the image to analyze local data"
keypoints:
---

### Pulling and image
Let's pull (download) an image:
`docker pull bids/base_fsl`

Where is this image coming from? From [Docker Hub](https://hub.docker.com/r/bids/base_fsl/).

### Getting inside a container
Let's go `inside` the container (an instance of an image) and poke around:
`docker run -ti --rm bids/base_fsl`

A Linux shell prompt should appear (independently of your host operating system!). Play around. Can you answer the following questions:
- What user are you inside the container? Is it the same user as on your host computer?
- Can you run FSL tools such as `bet`?
- Can you access files from your host computer?
- Create some files inside the container. Get out of the container (type `exit`). Run the container again. Are the files still there?
