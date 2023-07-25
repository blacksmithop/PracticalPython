---
description: Perform NLP tasks with spark-nlp
---

# ⚡ Spark NER

Apache offers a powerful data processing engine called Spark. We can leverage this tool using Python with Spark NLP library.

Start off by installing the packages

```json
pip install spark-nlp==4.2.8
```

### NER Pipeline

Data goes through various processes in an ML project. There could be pre-processing, normalizing, model fitting a so on. Defining each stage manually can be tedious. This is where Pipelines come into play.

We define a sequence of steps the data must take to get the desired output

```python
from pyspark.ml import Pipeline
```

{% hint style="info" %}
Any ML library worth its salt offers a mechanism for defining Pipelines, check therm out!
{% endhint %}

```python
from sparknlp.annotator import (
    WordEmbeddingsModel,
    BertEmbeddings,
    NerDLModel,
    NerConverter,
    Tokenizer,
    T5Transformer,
)

# We are passing input as documents or lists of text
documentAssembler = (
    DocumentAssembler().setInputCol("text").setOutputCol("document")
)

# Next, we tokenize the texts
tokenizer = Tokenizer().setInputCols(["document"]).setOutputCol("token")

# Define an Embedding step
embeddings = (
                WordEmbeddingsModel.pretrained("glove_100d")
                .setInputCols(["document", "token"])
                .setOutputCol("embeddings")
            )

# Neural Network based NER Model
ner_model = (
    NerDLModel.pretrained(MODEL_NAME, "en")
    .setInputCols(["document", "token", "embeddings"])
    .setOutputCol("ner")
)


# Converts the output to human readable format
ner_converter = (
    NerConverter()
    .setInputCols(["document", "token", "ner"])
    .setOutputCol("ner_chunk")
)

nlp_pipeline = Pipeline(
        stages=[
            self.documentAssembler,
            self.tokenizer,
            self.embeddings,
            self.ner_model,
            self.ner_converter,
        ]
    )
```

It is to be noted that for running Spark NLP you need a Java Runtime as well as Spark. Testing on Google Colab is recommended.
