# 🤝 Get Access Token

We'll be making our requests through the Graph API

* Define our`authority` url

```python
authority_url = f'https://login.microsoftonline.com/{tenant_name}'
```

* Remember those credentials we grabbed earlier?

Now we define the app

{% code lineNumbers="true" %}
```python
import msal
```
{% endcode %}

{% code title="get_access_token.py" overflow="wrap" lineNumbers="true" %}
```python
def acquire_token():
    """
    Acquire token via MSAL
    """

    tenant_name = "tenant-name"
    authority_url = f'https://login.microsoftonline.com/{tenant_name}'

    app = msal.ConfidentialClientApplication(
        authority=authority_url,
        client_id=getenv('CLIENT_ID'),
        client_credential=getenv('CLIENT_SECRET')
    )

    token = app.acquire_token_for_client(scopes=["https://graph.microsoft.com/.default"])

    print("Token obtained:", ["No", "Yes"][token["access_token"] != ""])

    return token
```
{% endcode %}

We can use this token to access the Graph API as below

```python
from office365.graph_client import GraphClient
```

```python
client = GraphClient(acquire_token)
```
