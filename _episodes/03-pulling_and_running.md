---
title: "Pulling and running a container"
teaching: 0
exercises: 15
questions:
objectives:
- "Pull (download) an image from Docker Hub"
- "Run shell inside a container"
- "Mount local folders"
- "Apply software from the image to analyze local data"
keypoints:
- "Container images are downloaded from Docker Hub."
- "You can run shell inside the container."
- "Only explicitly mounted host folder are accessible inside the container."
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
- Is there a '/data' folder inside the container?

### Accessing local files

Before we try to access files from the localhost lets get some example data

1. Create a folder on your local machine. I went with `/home/me/docker_tutorial`
2. Go to [NeuroVault.org](http://neurovault.org) pick a map (for example [this one](http://neurovault.org/media/images/457/tfMRI_SOCIAL_TOM-RANDOM_zstat1.nii.gz) and download it to the example folder.

Let's mount this folder so it will be accessible from the container when we run it
`docker run -ti --rm -v /home/me/docker_tutorial:/data bids/base_fsl`

Excercises:

1. Can you see the downloaded map in `/data` folder inside the container?
2. Can you use tools installed in the container on the files in the `/data` folder? For example `fslmaths /data/tfMRI_SOCIAL_TOM-RANDOM_zstat1.nii.gz -kernel gauss 10 -fmean /data/smoothed.nii.gz`
3. After getting out of the container can you see the modified files on your host system?
