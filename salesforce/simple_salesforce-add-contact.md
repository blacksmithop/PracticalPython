---
description: Add contacts to List
---

# 🧑🦰 simple\_salesforce: Add Contact

Create a new contact with some metadata

{% code title="Add new Contact" overflow="wrap" lineNumbers="true" %}
```python
from simple_salesforce import Salesforce
from typing import List


def populate_contacts(obj: Salesforce):
    responses: List[dict] = []

    contacts: List[dict] = [
        dict(LastName="Smith", Email="smith@example.com", Phone=5782239340),
        dict(LastName="John", Email="john@example.com", Phone=2312659340),
        dict(LastName="Adam", Email="adam@example.com", Phone=6593404388),
    ]
    
    for contact in contacts:
        resp = obj.Contact.create(contact)

        responses.append(resp)

    return responses
```
{% endcode %}

To run this function pass an instance of `Salesforce` to it

```python
resp = populate_contacts(sf)

print(resp)
```

<figure><img src="../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>
