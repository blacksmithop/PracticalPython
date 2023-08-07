---
description: Run your FastAPI server behind a Nginx proxy
---

# ⚡ FastApi with Nginx

### Create FastApi application

{% code title="main.py" overflow="wrap" lineNumbers="true" %}
```python
from fastapi import FastAPI

app = FastAPI()


@app.get("/")
def read_root():
    return {"message": "It's working!"}
```
{% endcode %}

Run this as a docker container. See [https://github.com/blacksmithop/FastAPI\_Docker](https://github.com/blacksmithop/FastAPI\_Docker)

### Run nginx as a docker container

```sh
docker run -d --name nginx-base -p 80:80 nginx:latest
```

### Configure nginx to act as reverse proxy

Copy the config file to your local directory

```sh
docker cp nginx-base:/etc/nginx/conf.d/default.conf LOCAL_PATH/default.conf
```

### Create a network in docker

```sh
docker network create nginx-fastapi
```

### Add containers to network

```sh
docker network connect nginx-fastapi nginx-base
docker network connect nginx-fastapi fastapi-app
```

Get IP address of FastApi App

```shell
docker network inspect nginx-fastapi
```

Add this to config file copied earlier

{% code title="default.conf" overflow="wrap" lineNumbers="true" %}
```roboconf
server {
    listen       80;
    server_name  localhost 192.168.100.135;


    location /directory {
        proxy_pass http://172.19.0.3/16;
    }
}
```
{% endcode %}

Copy this to container

```sh
docker cp LOCAL_PATH/default.conf nginx-base:/etc/nginx/conf.d/
```

Check syntax and reload nginx

```sh
docker exec nginx-base nginx -t
docker exec nginx-base nginx -s reload
```

