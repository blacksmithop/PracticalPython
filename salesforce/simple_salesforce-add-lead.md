# 😗 simple\_salesforce: Add Lead

```python
from simple_salesforce import Salesforce
from typing import List


def populate_leads(obj: Salesforce):
    responses: List[dict] = []

    leads: List[dict] = [
        dict(LastName="John Doe", Email="doe@example.com", Phone=5782239340, Company="ABC Corp"),
        dict(LastName="Adam Richard", Email="richard@example.com", Phone=2312659340, Company="ABC Corp"),
        dict(LastName="Ullyses Clark", Email="clark@example.com", Phone=6593404388, Company="ABC Corp"),
    ]
    
    for lead in leads:
        resp = obj.Lead.create(lead)

        responses.append(resp)

    return responses
```
