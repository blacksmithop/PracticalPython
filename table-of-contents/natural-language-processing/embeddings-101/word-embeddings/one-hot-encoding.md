# 🔴 One-hot encoding

Let's say we have a piece of text

```python
text = "the cat sat on the mat"
```

We can one-hot encode this by creating a zero vector with length equal to the _Vocabulary_&#x20;

```python
words_in_text = text.split()
print(words_in_text)
# ['the', 'cat', 'sat', 'on', 'the', 'mat']
```

***

```python
one_hot_encoding = [[] for _ in words_in_text]
# [[], [], [], [], [], []]
```

Now we populate it with the encoding

```python
idx = 0

sorted_words_in_text = sorted(words_in_text)

for word in words_in_text:
  for s_word in sorted_words_in_text:
    one_hot_encoding[idx].append(int(word==s_word))
  idx += 1
```

```python
import numpy as np

print(np.matrix(one_hot_encoding))
```

```json
[[0 0 0 0 1 1]
 [1 0 0 0 0 0]
 [0 0 0 1 0 0]
 [0 0 1 0 0 0]
 [0 0 0 0 1 1]
 [0 1 0 0 0 0]]
```

We can tabulate this with _tabulate_

{% code overflow="wrap" %}
```python
one_hot_encoding_label = [[label] + sub_list for label, sub_list in zip(words_in_text, one_hot_encoding)]
```
{% endcode %}

{% code overflow="wrap" %}
```python
from tabulate import tabulate

print(tabulate(one_hot_encoding_label, headers=[""] + sorted_words_in_text), end="")
```
{% endcode %}

```
       cat    mat    on    sat    the    the
---  -----  -----  ----  -----  -----  -----
the      0      0     0      0      1      1
cat      1      0     0      0      0      0
sat      0      0     0      1      0      0
on       0      0     1      0      0      0
the      0      0     0      0      1      1
mat      0      1     0      0      0      0
```

\
