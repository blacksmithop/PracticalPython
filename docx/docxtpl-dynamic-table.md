# 📖 docxtpl - Dynamic table

Use jinja to dynamically render data in word (docx) files

{% embed url="https://colab.research.google.com/drive/1On8WaSnMAtdY0JqDDmzU-XiW6i6Bz_Tj?usp=sharing" %}
See it in action
{% endembed %}

## Create a template

{% file src="../.gitbook/assets/template.docx" %}
template file
{% endfile %}

Create a word document with a template

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

{% code title="Install docxptl" %}
```sh
pip install docxtpl
```
{% endcode %}

{% code title="Write list of dicts to a docx template" overflow="wrap" lineNumbers="true" %}
```python
from docxtpl import DocxTemplate
import jinja2

tpl = DocxTemplate('template.docx')

context = {
    'frameworks': [
        {
            'title': 'this is line # 1',
            'desc': 'Lorem ipsum dolor sit amet.',
        },
        {
            'title': 'this is line # 2',
            'desc': 'Rem nemo ipsam id facilis molestias et enim in pariatur voluptas sed temporibus illo dolor quibusdam.',
        },
        {
            'title': 'this is line # 3',
            'desc': 'A cupiditate esse et dolores temporibus sed sequi nisi cum voluptatem praesentium et odit voluptatem.',
        },
    ],
}
jinja_env = jinja2.Environment(autoescape=True)
tpl.render(context, jinja_env)
tpl.save('test-result.docx')
```
{% endcode %}

## Output

{% file src="../.gitbook/assets/test-result.docx" %}
Output file
{% endfile %}

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

Script

```python
from docxtpl import DocxTemplate
import jinja2

tpl = DocxTemplate('template.docx')

context = {
    'frameworks': [
        {
            'title': 'this is line # 1',
            'desc': 'Lorem ipsum dolor sit amet.',
        },
        {
            'title': 'this is line # 2',
            'desc': 'Rem nemo ipsam id facilis molestias et enim in pariatur voluptas sed temporibus illo dolor quibusdam.',
        },
        {
            'title': 'this is line # 3',
            'desc': 'A cupiditate esse et dolores temporibus sed sequi nisi cum voluptatem praesentium et odit voluptatem.',
        },
    ],
}
jinja_env = jinja2.Environment(autoescape=True)
tpl.render(context, jinja_env)
tpl.save('test-result.docx')
```
