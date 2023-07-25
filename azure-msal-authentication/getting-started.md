# 🟢 Getting started

## Microsoft Authentication Library for Python

1. &#x20;Create an App in Azure Active Directory
2. &#x20;Configure the necessary permissions. [SharePoint example](broken-reference)
3. &#x20;Grab the `Client ID`, `Client Secret,` and `App ID`

### Start off by getting your tenant name

```python
tenant_name = "tenant-name-in-login-url"
```

{% hint style="info" %}
This can be `common` if we're using our personal account, for organizations try signing into a service like Outlook.\
Eg: `https://login.microsoftonline.com/tenant-name-goes-here`&#x20;
{% endhint %}

Define a `.env` file with those credentials

```json
CLIENT_ID=your-client-id
CLIENT_SECRET=your-client-secret
```
