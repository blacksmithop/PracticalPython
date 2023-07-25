---
description: Salesforce REST api client
---

# 😁 simple\_salesforce

## Getting started

First, create a Salesforce Connected App with OAuth enabled

Now install the REST api client and python-dotenv (secret management)

```sh
pip install simple_salesforce python-dotenv
```

## Usage

Make note of the Consumer Key and Secret we'll be authenticating with those

{% code title="authenticate.py" overflow="wrap" lineNumbers="true" %}
```python
from simple_salesforce import Salesforce
from dotenv import load_dotenv
from os import getenv
import requests

from utils.create_contacts import populate_contacts

load_dotenv()
session = requests.Session()


sf = Salesforce(username=getenv("EMAIL"), password=getenv("PWD"),
                consumer_key=getenv("CONSUMER_KEY"), consumer_secret=getenv("CONSUMER_SECRET"),
                session=session)
```
{% endcode %}
