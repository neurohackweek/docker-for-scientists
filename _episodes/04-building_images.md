---
title: "Creating your own docker images"
teaching:
exercises: 10
questions:
- "How can I build my own images?"
objectives:
- "Learn how to create Docker images"
keypoints:
- "Container images are build using simple recipes - Dockerfiles."
---

## Creating Docker images

Docker images are created using simple recipe files called Dockerfiles. Let's create a Dockerfile. Open your favourite editor and type the following text, and save it under the name `Dockerfile` (no extensions) **inside an empty folder**.

```
FROM bids/base_fsl
RUN wget http://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh -O /opt/miniconda.sh
RUN /bin/bash /opt/miniconda.sh -b -p /opt/conda
ENV PATH="/opt/conda/bin:$PATH"
```

Open a terminal in the same directory and run the following command:

`docker build -t fsl_with_conda .`

Don't forget about the dot at the end! It indicates the directory where Docker will look for a Dockerfile - in our case it's the current working directory. This should build your image. You can run it like the previous one:

`docker run -ti --rm fsl_with_conda`

Exercises:

1. Can you run python inside the container?
2. What happens if you run the build command again?
3. Could you modify your Dockerfile to include extra python packages?
4. When you rebuild your image did you notice something unusual?
