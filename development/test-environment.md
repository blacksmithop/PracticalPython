---
description: Use docker containers as your staging environment
---

# 🤖 Test Environment

## <mark style="color:green;">Pull</mark> image

```sh
docker pull ubuntu
```

## <mark style="color:yellow;">Create</mark> a container

```sh
docker run -it --name ubuntu_dev ubuntu
```

{% hint style="info" %}
Ensure your `ubuntu_dev` is running with docker ps.\
If not start it again. This is important!
{% endhint %}

## <mark style="color:purple;">Open</mark> terminal in container

```sh
docker exec -it ubuntu_dev bash
```
