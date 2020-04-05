---
title: "Building Docker Image for an existing Flask project"
date: 2020-04-03
permalink: /posts/2020/04/blog-post-1/building-docker-existing-flask-project
redirect_from: /posts/2020/04/blog-post-1/
tags:
  - docker
  - flask
  - python
  - containerization
---

This was my attempt to get used to the docker environment and build images on the fly with my future and current projects. I used my old Flask project which had Sentiment Analysis as ML model and Flask server to host it. However the deployment of the ML model can be done in different ways like TF-Serving and stuff but since I wanted to get my hands dirty with docker I chose to do it in that way. 

I started with setting out my virtual environment in Python with all dependencies required to run the project seamlessly. This is first step and kind of crucial so if you don't have a virtual environment set head over to [python-venv](https://docs.python.org/3/library/venv.html) to set it right up.
After installing all the dependencies using pip run
```
pip freeze > requirements.txt
```

This will make a requirements.txt file in that dir containing all the dependencies with their versions you used to run your project. This step is important since Docker Image is a snapshot of your running env. 
After successfully creating venv and requirements file create a DOCKERFILE in the project dir 

<script src="https://gist.github.com/theAayushbajaj/c17d74fea7e2c2d6b1cb8d4eb1698786.js"></script>

`Line 1`: Get an image of ubuntu:18.04 from the docker-hub<br/>
`Line 3`: Specify a workding directory. Note that all the commands like COPY, RUN will be executed in this.<br/>
`Line 5-6`: Installing the python development files and updating the system.<br/>
`Line 8`: Copy the requirements file from the current directory to the WORKDIR of the docker image.<br/> 
`Line 10`: executing the pip install on requirements file.<br/>
`Line 12`: Copy the rest of the code file to the WORKDIR<br/>
`Line 14-16`: Execute the index.py (Flask server file) upen entry.<br/>


Now run the following command to build the image of the project

```
docker build -t <Image name>:latest .
```
What this will do is execute the DOCKERFILE that contains all the instructions to build an image. Don't forget to replace <> with your name of the image. This command will take a while to run.

After this you've create a container of the image which will run your project. To create a container run

```
docker run --name <container name> -v "$(pwd)":/home -p5000:5000 <image name>:latest
```
This will make a container of that image and your Flask server will be up.

**Tip:**Make your Flask server to point to 0.0.0.0:port instead of 127.0.0.1