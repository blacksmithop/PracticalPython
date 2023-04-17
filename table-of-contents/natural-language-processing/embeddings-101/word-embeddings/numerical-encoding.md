# Numerical encoding

Given a piece of text

```python
text = "the cat sat on the mat"
```

We can encode each word with a unique number

For this example we will sort the words and then encode them with their index + 1

```python
words = text.split()
sorted_words = sorted(words)

print(f"{words=}\n{sorted_words=}")
#words=['the', 'cat', 'sat', 'on', 'the', 'mat']
#sorted_words=['cat', 'mat', 'on', 'sat', 'the', 'the']
```

<pre class="language-python"><code class="lang-python">sorted_words = list(set(sorted_words))

<strong>num2char = {word[0]:idx for idx, word in enumerate(sorted_words, start=1)}
</strong>
print(num2char)
#{'c': 1, 'm': 2, 'o': 3, 's': 4, 't': 5}
</code></pre>

Using this dictionary we can map the words to their numerical values

```python
[num2char[w[0]] for w in words]
#[5, 1, 4, 3, 5, 2]
```

The benefit of doing so over [One-hot encoding](one-hot-encoding.md) is that this leaves us with a dense vector of merely 6 integers instead of a sparse vector with 6 vectors in them!
