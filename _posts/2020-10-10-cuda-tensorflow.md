---
title: "Solving Cuda 10.1,10.2 missing library problem with Tensorflow 2"
date: 2018-12-17
permalink: /posts/2020/10/blog-post-8/solving-cuda-tf2
redirect_from: /posts/2020/10/blog-post-8/
tags:
  - Cuda
  - Tensorflow 2
---

Configuring Tensorflow 2 to run with GPU is truely a cumbersome task. Part of the problem is for you code to run on GPU there's whole pipeline that is needed to followed, from creating memory buffers to placing variables. This is done by a low level library such as CUDA and high level abstraction is provided by Tensorflow.

Issue to set the right version and multiple compatibility checks. CUDA and Tensorflow are maintained by two different companies and have no collaboration as such, so the versioning issue is bound to arise.

I was stuck in this problem for hours trying to get Tensorflow 2 to utilize GPU, tried couple different CUDA versions viz 10.1,10.2 but both of them gave me some library missing issue, particularly libcublas(in 10.1), libcudart and some other. So I devised a fix for this.

A simple solution is to download (tested on Tensorflow 2.2.0 and 2.3.0) both version of CUDA i.e 10.1 and 10.2 or 10.0, keep 10.1 as default and create symlinks for the missing files after running some tf function. These versions are very similar so bin from either versions will work with each other.


However, you can also just download the required binaries from the repository and create symlinks. I'll link a dir containing the most common missing binaries in CUDA 10.1

Note that this is just a fix to get things working. Please apply symlinks carefully.
```
sudo ln -s /usr/local/cuda-10.2/targets/x86_64-linux/lib/libcublas.so.10.1 /path/to/missing-files/libcublas.so.10.0
```

It is advised to store the missing files seperately in a directory and create symlinks accordingly, it'll help you idenitfy the linked files in the future. Find them missing binaries [here](https://github.com/superjamie/lazyweb/wiki/Raspberry-Pi-3.5mm-Audio-Hiss).
