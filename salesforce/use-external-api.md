---
description: Use external api services in LWC and Salesforce
---

# 🌏 Use External API

### Add Named Credentials

<figure><img src="../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

### Select Legacy

![](<../.gitbook/assets/image (18).png>)

### Add details

<figure><img src="../.gitbook/assets/image (47).png" alt=""><figcaption></figcaption></figure>

### Add URL to CSP

<figure><img src="../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

### Finally, register an External Service

<figure><img src="../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>

### Select from API Specification

<figure><img src="../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

### Add the API Specification

<figure><img src="../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

The schema can be:

1. An absolute URL
2. Relative URL where schema json is hosted
3. Schema in JSON format
4. Schema uploaded as a file

{% hint style="info" %}
Schema must be OpenAPI Version 2 compilant
{% endhint %}

OpenAPI Version 2 Schema

{% embed url="https://fastapi-vercel-serverless-indol.vercel.app/static/schema.json" %}

OpenAPI Version 3 Schema

{% embed url="https://fastapi-vercel-serverless-indol.vercel.app/openapi.json" %}

### FastAPI API Service



{% swagger src="https://sfpocqaapi.mykoldatabase.com/openapi.json" path="/" method="get" %}
[https://sfpocqaapi.mykoldatabase.com/openapi.json](https://sfpocqaapi.mykoldatabase.com/openapi.json)
{% endswagger %}

{% swagger src="https://sfpocqaapi.mykoldatabase.com/openapi.json" path="/api/insert_insight" method="post" %}
[https://sfpocqaapi.mykoldatabase.com/openapi.json](https://sfpocqaapi.mykoldatabase.com/openapi.json)
{% endswagger %}

{% swagger src="https://sfpocqaapi.mykoldatabase.com/openapi.json" path="/interaction-details/" method="get" %}
[https://sfpocqaapi.mykoldatabase.com/openapi.json](https://sfpocqaapi.mykoldatabase.com/openapi.json)
{% endswagger %}
