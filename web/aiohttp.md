---
description: Make web apps with just aiohttp
---

# 🕸 aiohttp

Most know of this library as an asynchronous substitute for the `requests` library. Useful when you discord.py bot or FastAPI route needs that non-blocking http request.



What if you could make a whole web app with just this library?

```python
from aiohttp import web
import aiohttp_jinja2
import jinja2
from aiohttp.web import middleware
from endpoints.endpoint import app_routes

from os import environ

routes = web.RouteTableDef()


@middleware
async def middleware(request, handler):
    try:
        resp = await handler(request)
        return resp
    except web.HTTPException as e:
        if e.status == 404:
            return aiohttp_jinja2.render_template('404.html', request, context=None)
        if e.status == 500:
            return aiohttp_jinja2.render_template('500.html', request, context=None)

app = web.Application(middlewares=[middleware])


@routes.get('/')
async def index(request):
    return aiohttp_jinja2.render_template('index.html', request, context=None)


if __name__ == '__main__':
    app.add_routes(routes)
    app.add_routes(app_routes)
    app.add_routes(app_routes2)
    
    app.router.add_static('/assets/',
                          path='./views/assets',
                          name='assets')
                          
    aiohttp_jinja2.setup(app, loader=jinja2.FileSystemLoader('./views'))
    
    port = int(environ.get('PORT', 8080))
    
    web.run_app(app, port=port)
```

{% hint style="info" %}
Your html templates would go inside a folder name `views`
{% endhint %}

> endpoints/endpoint.py

```python
from aiohttp import web

app_routes = web.RouteTableDef()


@app_routes.get("/route_name")
async def abandon(request):
    return web.Response(text="hi")
```

> index.html

```django
<head>
  {% raw %}
{% include "partials/header.html" %}
{% endraw %}
</head>
<body>
  <div class="content">
      Hello World
    </div>
  </div>
</body>
```

> partials/header.html

```django
<title>Indes</title>
<meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
<link rel="stylesheet" href="/assets/style.css" type="text/css">
```

> assets/style.css

```django
body {
  margin: 0;
  background-color: #2C2E33;
  font-family: 'Montserrat', sans-serif;
}
```
