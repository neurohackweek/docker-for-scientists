---
title: "Running containers on clusters and HPCs"
teaching: 5
exercises: 0
questions:
- "How can I run my containers on clusters/HPCs if my admin refuse to install Docker?"
objectives:
- "Learn how to use Singularity"
keypoints:
- "You can use Singularity to run containers on multitenant systems."
---

## Running containers on clusters and HPCs

Docker works great on modern operating systems in a single tenant scenarios. However, due to kerl feature requirements and the need for elevated security
it is hard sell for administrators of academic clusters. All of the reasons for the deal breaker Docker requirements are for functionality (networking, resource sandboxing etc.)
that are not crucial in context of academic use. A different container framework [Singularity](http://singularity.lbl.gov/) provides ability to run containers without
the need for special kernel versions or security workarounds. It still needs to be installed on the cluster, but it's much more popular among HPC admins
(ask your admin if they could install it!).

To run your image on the cluster:
`singularity shell --cleanenv docker://filo/fsl_with_conda`

You probably notice that each time we run this command a few slow conversion operations happen.
We can also download the image to reuse it later with shorter start time
`singularity build /tmp/my_container.img docker://filo/fsl_with_conda`

Then we can reuse this image with:
`singularity shell --cleanenv /tmp/my_container.img`
