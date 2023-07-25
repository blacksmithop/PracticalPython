# 🗝 OAuth2 Authorization

{% hint style="info" %}
`tenant_name` would be the alphanumerical value unique to Microsoft apps used by your organization
{% endhint %}

{% code title="oauth_grant.py" overflow="wrap" lineNumbers="true" %}
```python
from requests_oauthlib import OAuth2Session
from oauthlib.oauth2 import MobileApplicationClient

from dotenv import load_dotenv
from os import getenv

load_dotenv()

tenant_name = "tenant-name"

scopes = ['Sites.ReadWrite.All','Files.ReadWrite.All']

auth_url = f'https://login.microsoftonline.com/{tenant_name}/oauth2/v2.0/authorize'

#MobileApplicationClient is used to get the Implicit Grant
oauth = OAuth2Session(client=MobileApplicationClient(client_id=getenv("client_id")), scope=scopes)

authorization_url, state = oauth.authorization_url(auth_url)
authorization_link = oauth.get(authorization_url)

print(authorization_link.url)
```
{% endcode %}
