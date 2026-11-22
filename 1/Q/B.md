### **1. What is a Pipeline in Hugging Face?**

A `pipeline` is a high-level API provided by Hugging Face Transformers that simplifies the process of performing machine learning tasks.

Instead of manually writing all the steps for:

* Loading a model.
* Processing input text.
* Passing input through the model.
* Generating output.
* Decoding the output.

We can use a pipeline that handles much of this automatically.


### **2. Why are we using it here?**

We want our fine-tuned Llama 2 model to generate text.

Hugging Face provides different pipelines for different tasks:


| Pipeline task         | Purpose                        |
| --------------------- | ------------------------------ |
| `text-generation`     | Generate text using an LLM     |
| `text-classification` | Classify text into categories  |
| `summarization`       | Summarize text                 |
| `translation`         | Translate languages            |
| `question-answering`  | Answer questions using context |


### **3. What does this line do?**

```
pipeline = transformers.pipeline(
```

* `transformers.pipeline()` calls the pipeline function.
* `pipeline` stores the initialized pipeline object.
* The arguments inside the parentheses specify which task and model to use.

**Important:** At this point, we are initializing the pipeline. The model is loaded through this function using the model repository we specify in the following arguments.


### **2. What happens in text generation?**

Suppose our input is:

```
prompt = "What is a large language model?"
```

The model processes this input and predicts the next tokens one by one to construct a response.


**Q1. What is text generation in Generative AI?**

It is the process of generating new text based on an input prompt using a trained language model.

**Q2. How does an autoregressive LLM generate text?**

It predicts the next token based on previously available tokens and continues this process until a stopping condition is reached.

**Q3. Is text generation the same as text classification?**

No.

* Text generation produces new text.
* Text classification assigns a category or label to input text.


**Q1. What is the difference between a model and a tokenizer?**

* Model: Processes numerical inputs and generates predictions.
* Tokenizer: Converts text into token IDs and decodes token IDs into text.

**Q2. Does **`model=model`** perform fine-tuning?**

No. It loads an already fine-tuned model for inference.

**Q3. Where are model weights stored?**

They are stored in the model repository on Hugging Face or in a local model directory.
