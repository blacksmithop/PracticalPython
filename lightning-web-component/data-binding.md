---
description: Pass data between your frontend (html) and backend (js)
---

# 🖖 Data Binding

<figure><img src="../.gitbook/assets/image (24).png" alt="" width="375"><figcaption><p>Visualized</p></figcaption></figure>

With Lightning you have two ways of binding data between your template and js file

### 1. Using Expressions

Start off by creating a template

```html
<template>
    Hello {name}
</template>
```

Next, define a variable in your `.js` file

```javascript
import { LightningElement } from 'lwc';

export default class InteractionRecord extends LightningElement {
    name = "Abhinav";
}
```

<figure><img src="../.gitbook/assets/image (57).png" alt=""><figcaption><p>Output</p></figcaption></figure>

### Use getters

