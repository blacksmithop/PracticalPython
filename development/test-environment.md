---
description: Use docker containers as your staging environment
---

# 🤖 Test Environment

## <mark style="color:green;">Pull</mark> image

```sh
docker pull ubuntu
```

## <mark style="color:yellow;">Create</mark> container

```sh
docker run --name ubuntu_dev ubuntu
```

## <mark style="color:purple;">Open</mark> terminal in container

```sh
docker exec -it ubuntu_dev bash
```
