---
title: "Storing your containers on Docker Hub"
teaching: 10
exercises: 5
questions:
- "Where can I store my containers?"
objectives:
- "Learn how to upload your containers to Docker Hub"
keypoints:
- "You can store containers for your projects on Docker Hub and retrieve them at any time."
---

## Sharing/storing containers

Using containers locally is great, but what if you lost your workstation and would like to
quickly retrieve your container? Or what if you would like to share your container with collaborators?

You can upload your containers to a **public** repository called [Docker Hub](https://hub.docker.com).
It's a free and unlimited service, but requires your to first register [here](https://hub.docker.com/).
After registering you need to log in in your console:

```
docker login
```

Docker Hub takes container image names very seriously. Each image name has two components
username and image name: `<username>/<image_name>`. For example `filo/fsl_with_r`.
To be able to upload an image to Docker Hub we need to rename it appropriately. In the folder without
our `Dockerfile` we can add a new alias to our image:

```
docker build -t `<username>/fsl_with_r .`
```

Now we are ready to upload the image:

```
docker push `<username>/fsl_with_r`
```

After this process is finished we will be able to see the image listed on Docker Hub. For me
this will be at [https://hub.docker.com/u/filo/](https://hub.docker.com/u/filo/).

But does this work? Can I retrieve the image? Lets remove the local copy first

```
docker rmi fsl_with_r <username>/fsl_with_r
```

Exercises:
1. Can you run `fsl_with_r`?
2. What about `<username>/fsl_with_r`?
