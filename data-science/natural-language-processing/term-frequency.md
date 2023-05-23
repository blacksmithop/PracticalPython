# 🔢 Term Frequency

Suppose we have a document that is part of a corpus. Each document can be thought of as a collection of words. It can be useful to know how many times a certain word appears in a document.

This is referred to as Term Frequency

<div data-full-width="true">

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption><p>Equation</p></figcaption></figure>

</div>

It's the ratio of the _number of times_ a word is a document to the _total number_ of words

## Example:

```python
doc = "The quick brown fox jumped over the lazy dog as the dog was not quick"
```

{% hint style="info" %}
Here we are dealing with a piece of text without any punctuation so we'll forego any pre-processing. Real data is rarely so simple
{% endhint %}

We start off by splitting the string by whitespace

{% code title="Split by whitespace" overflow="wrap" lineNumbers="true" %}
```python
words = doc.split(" ")
print(words)
# ['The', 'quick', 'brown', 'fox', 'jumps', 'over', 'the', 'lazy', 'dog', 'as', 'the', 'dog', 'was', 'not', 'quick']
```
{% endcode %}

Now, we get the count of each word in the list. For this we use `Counter` from `collections` library

{% code title="Get word count with Counter" overflow="wrap" lineNumbers="true" %}
```python
from collections import Counter

tf = Counter(words)
print(tf)
# Counter({'quick': 2, 'the': 2, 'dog': 2, 'The': 1, 'brown': 1, 'fox': 1, 'jumps': 1, 'over': 1, 'lazy': 1, 'as': 1, 'was': 1, 'not': 1})
```
{% endcode %}

Use `pprint` to pretty print this

```python
from pprint import pprint

pprint(c)

>>Counter({'quick': 2,
         'the': 2,
         'dog': 2,
         'The': 1,
         'brown': 1,
         'fox': 1,
         'jumps': 1,
         'over': 1,
         'lazy': 1,
         'as': 1,
         'was': 1,
         'not': 1})
```

