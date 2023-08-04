---
description: Convert your python applications into docker containers
---

# 📦 Dockerize your python application

### 1. Create a `Dockerfile`

`Dockerfile` syntax

```dockerfile
# syntax=docker/dockerfile:1

FROM python:3.8-slim-buster

WORKDIR /code

# install dependencies

COPY ./requirements.txt /code/requirements.txt

RUN pip install --no-cache-dir --upgrade -r /code/requirements.txt

# Use cached packages if requirements haven't changed

COPY ./app /code/app

COPY ./static /code/static

EXPOSE 8080

CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "80"]
```

| Instruction | Desciption                                                                                               |
| ----------- | -------------------------------------------------------------------------------------------------------- |
| FROM        | The base image to use for our container, for a python application this can be `python:buster`            |
| WORKDIR     | This is the working directory for our application. We copy our application code to this folder           |
| COPY        | Copy files and folders to working directory, files can be ignore by creating a `.dockerignore` file      |
| EXPOSE      | The port we want the docker container to expose, we forward this to an external port eg `5000` -> `8080` |
| CMD         | The command to run your python application                                                               |

### 2. Create a `docker-compose.yml`

```yml
version: '1'

services:

  service_name:
    container_name: PythonApiService
    build: .
    image: author/name_of_image
    
    ports:
      - "80:80"

    volumes:
      - .:/code

    environment:
      API_KEY: <api_key>
```

### 3. Docker compose

```sh
docker compose up -d
```

Builds a image and runs the container based on your `Dockerfile`. The `-d` stands for detached here.

**Example:**

<figure><img src=".gitbook/assets/image (1) (1) (1).png" alt=""><figcaption><p>Images</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (1) (1).png" alt=""><figcaption><p>Containers</p></figcaption></figure>

This container can now be accessed at http://localhost:80

#### How to manually deploy your Docker container

Firstly `cd` into the directory which has the `Dockerfile`

**1. Create an image with**

`docker build -t author/image_name .`

**2. Run the container with required parameters**

`docker run -d --name container-name -e API_KEY=<api-key> -p 80:80 author/image_name`

| Argument | Description                                                                                                                    |
| -------- | ------------------------------------------------------------------------------------------------------------------------------ |
| `-e`     | Environment variables to be used inside your container, like api-keys, database names, connection strings etc                  |
| `-p`     | Port mapping from your host to the docker network eg: `-p host-port:container-port`                                            |
| `-d`     | Tells docker to run this container detached. You will need Docker desktop (Windows) or use `docker logs` to see container logs |
