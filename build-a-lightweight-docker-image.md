# 💡 Build a lightweight docker image

For most Python apps it is often enough to simply use a `slim-buster` [image ](https://hub.docker.com/\_/python)or even an `alpine` one.&#x20;

However, sometimes you need an additional package or two that doesn't come with these images.

While you could sometimes work your way around some issues by having a file locally, or download a .deb file or so, it is not always possible. It is all too easy to end up with a messy `Dockerfile`

We can avoid many such pitfalls by starting off from a slim OS image like Alpine



The problem with alpine is that it lacks many of the core features you'd expect to find in Ubuntu and as such docker builds take forever.

Here's a relatively lightweight Docker image with Ffmpeg and Python

```docker
FROM ubuntu:20.04

RUN apt update
RUN apt install -y software-properties-common
RUN add-apt-repository ppa:deadsnakes/ppa

RUN apt-get update
RUN apt install -y ffmpeg
RUN apt-get install -y python3-distutils

WORKDIR /code

COPY ./get-pip.py /code/get-pip.py

RUN python3 get-pip.py \
		--disable-pip-version-check \
		--no-cache-dir \
		pip \
		setuptools 
        
# install dependencies
COPY ./requirements.txt /code/requirements.txt
RUN pip install --no-cache-dir --upgrade -r /code/requirements.txt
```

You can download get-pip.py from [here](https://raw.githubusercontent.com/pypa/get-pip/3cb8888cc2869620f57d5d2da64da38f516078c7/public/get-pip.py)
