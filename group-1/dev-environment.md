---
description: Use docker containers as your staging environment
---

# Dev Environment

## Pull image

```sh
docker pull ubuntu
```

## Create container

```sh
docker run --name ubuntu_dev ubuntu
```

## Open terminal in container

```sh
docker exec -it ubuntu_dev bash
```
