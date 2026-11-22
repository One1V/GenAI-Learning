## **Why can't an LLM directly process ordinary text?**

**Answer:** LLMs are neural networks that perform mathematical computations on numerical data. They cannot directly perform these computations on ordinary human-readable text.

Therefore, we convert text into numerical representations using a process called **tokenization**.

"LLMs cannot directly process ordinary text because neural networks perform mathematical operations on numerical data. Therefore, we use tokenization to convert text into token IDs, which are subsequently converted into embeddings and processed by the model."

The important point is that the model ultimately works with numerical tensors rather than raw strings.


## **What is the difference between a token and a token ID?**

This is a very important distinction.

**Token:** A piece of text produced by a tokenizer. It can be a complete word, part of a word, punctuation or another text unit.

**Token ID:** The unique integer assigned to that token in the tokenizer's vocabulary.

## **4. What is the purpose of AutoTokenizer?**

`AutoTokenizer` is a class provided by Hugging Face Transformers.

Its purpose is to automatically load the appropriate tokenizer configuration for a given pre-trained or fine-tuned model.

from transformers import AutoTokenizer

model = "entbappy/Llama-2-7b-chat-finetune"

tokenizer = AutoTokenizer.from_pretrained(model)

What happens here?

1. We provide the model repository name.
2. `from_pretrained()` retrieves the tokenizer configuration and vocabulary associated with that model.
3. The tokenizer becomes ready to convert text into token IDs and decode IDs back into text.


**Q1. What is Hugging Face?**

Hugging Face is an AI platform and ecosystem that provides pre-trained models, datasets and tools for developing machine learning and NLP applications.

**What are parameters in an LLM?**

Parameters are the numerical weights and biases learned during model training. They determine how the model processes inputs and generates outputs.


**Q1. What is **`from_pretrained()`**?**

A Hugging Face method used to load a previously saved model or tokenizer from a model repository or local directory.

**Q2. Why should we use the same tokenizer as the model?**

Because the model expects token IDs according to the vocabulary and tokenization scheme it was trained with. Using an incompatible tokenizer can produce incorrect input representations.

**Q3. Can a tokenizer convert token IDs back into text?**

Yes. We use:

```
tokenizer.decode(token_ids)
```

**Q4. Does loading a tokenizer load the model weights?**

No. This line loads the tokenizer, not the neural network weights.
