---
title: "Running containers on clusters and HPCs"
teaching: 10
exercises: 0
questions:
- "How can I run my containers on clusters/HPCs if my admin refuse to install Docker?"
objectives:
- "Learn how to use Singularity"
keypoints:
---

## Running containers on clusters and HPCs

Docker works great on modern operating systems in asingle tenant scenarios. However, due to kerl feature requirements and the need for elevated security 
it is hard sell for administrators of academic clusters. All of the reasons for the dealbreaker Docker requirements are for functionality (networking, resource sandboxing etc.)
that are not crucial in context of academic use. A different container framework [Singularity](http://singularity.lbl.gov/) provides ability to run containers without
the need for special kernel versions or security workarounds. It still needs to be installed on the cluster, but it's much more popular among HPC admins
(ask your admin if they could install it!).

Before running your Docker image on Singularity you need to convert it. **This operation requires root access and should be done on your local machine**.
The following command will create a singularity container:

```
 docker run \        
 -v /var/run/docker.sock:/var/run/docker.sock \
 -v D:\singularity:/output \
 --privileged -t --rm \
 filo/docker2singularity \            
 fsl_with_python
```

In contrast to Docker, Singularity stores images as single files. You will need to copy the .img file created by the converter to your cluster.
To run your image on the cluster:
`singularity run bids_example-0.0.4.img`
