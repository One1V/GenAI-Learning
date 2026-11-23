The next actual line is:

```
f'<s>[INST] {prompt} [/INST]',
```

### **1. What is happening here?**

We are passing the input prompt to the Llama 2 model in its expected **instruction format**.

Let's break it down:

```
f'<s>[INST] {prompt} [/INST]'
```


| Part                    | Meaning                                             |
| ----------------------- | --------------------------------------------------- |
| `<span>f</span>`        | Allows Python to insert a variable inside a string. |
| `<span><s></span>`      | Marks the beginning of the input sequence.          |
| `<span>[INST]</span>`   | Marks the beginning of an instruction.              |
| `<span>{prompt}</span>` | Inserts the actual prompt stored in the variable.   |
| `<span>[/INST]</span>`  | Marks the end of the instruction.                   |

### **2. What will the actual input look like?**

Earlier, we defined:

```
prompt = "What is a large language model?"
```

Python replaces `<span>{prompt}</span>` with that value.

So the final string becomes:

```
<s>[INST] What is a large language model? [/INST]
```

This tells Llama 2:

"Here is an instruction. Understand it and generate an appropriate response."

### **3. Why do we need this format?**

Llama 2 Chat models were trained to understand a particular conversation format.

If we provide instructions in the expected format, the model can interpret the user's request correctly.

**Interview point:** This is an example of prompt formatting using the Llama 2 instruction/chat template.

### **Quick question**

What does `<span>{prompt}</span>` do inside this f-string?

A. Loads the model.

B. Inserts the actual question into the string.

C. Fine-tunes the model.

D. Converts the question into embeddings.



The next actual line is:

```
do_sample=True,
```

### **1. What does **`<span>do_sample=True</span>`** mean?**

It controls **how the model selects the next token** while generating a response.

Remember, an LLM generates text one token at a time.

Suppose the model predicts these possibilities:


| Possible next token | Probability |
| ------------------- | ----------- |
| AI                  | 50%         |
| computer            | 30%         |
| technology          | 20%         |

* With `<span>do_sample=True</span>`, the model samples from the probability distribution instead of always selecting the highest-probability token.
* With `<span>do_sample=False</span>`, it generally uses greedy decoding and selects the highest-probability token.

### **2. Why use sampling?**

It can make responses more varied and less predictable.

For example, asking the same question multiple times may produce slightly different responses.

**Important:** Sampling does not mean randomly selecting any word. The selection is influenced by the model's predicted probabilities and other generation settings.

### **Interview-ready answer**

`<span>do_sample=True</span>` enables probabilistic token sampling during text generation, allowing the model to produce more diverse responses.

### **Quick question**

What happens when `<span>do_sample=True</span>`?

A. The model starts fine-tuning.

B. The model samples the next token from its probability distribution.

C. The model converts text into embeddings.

D. The model disables token generation.



The next actual line is:

```
top_k=10,
```

### **1. What does **`<span>top_k=10</span>`** mean?**

Remember, your Llama 2 model predicts possible next tokens while generating a response.

Suppose the model predicts these possibilities:


| Token        | Probability |
| ------------ | ----------- |
| AI           | 40%         |
| technology   | 25%         |
| computer     | 15%         |
| machine      | 10%         |
| learning     | 5%          |
| Other tokens | 5%          |

If we use `<span>top_k=3</span>`, the model considers only the **3 most likely tokens** for the next-token selection.

If we use `<span>top_k=10</span>`, it considers only the 10 highest-scoring candidate tokens.

**Visual example: Top 3 selection**

AI

40%

Selected

Technology

25%

Selected

Computer

15%

Selected

Machine

10%

Excluded

Learning

5%

Excluded

Illustrative probabilities, not actual Llama 2 output.

### **2. Why do we use it?**

It prevents the model from considering extremely unlikely tokens during sampling.

* Smaller `<span>top_k</span>` → fewer choices, potentially more predictable output.
* Larger `<span>top_k</span>` → more choices, potentially more diverse output.

**Important:**`<span>top_k</span>` works alongside `<span>do_sample=True</span>` in this notebook.

### **Interview-ready answer**

`<span>top_k</span>` is a text-generation parameter that restricts token sampling to the K most likely next-token candidates.

### **Quick question**

If `<span>top_k=5</span>`, how many candidate tokens are considered for the next-token selection?

A. All possible tokens.

B. Five most likely tokens.

C. Five complete sentences.

D. Five training examples.




Let's understand this line in detail:

```
num_return_sequences=1,
```

### **1. What does it mean?**

It tells the model **how many generated responses you want it to return for one input prompt.**

For example, suppose your prompt is:

```
prompt = "What is a large language model?"
```

If you use:

```
num_return_sequences=1
```

The model returns one generated response.

If you use:

```
num_return_sequences=3
```

The model returns three generated responses to the same prompt.

### **2. Visual example**

**One input prompt**

What is artificial intelligence?

`<span>num_return_sequences=3</span>`

Output 1

AI is the ability of machines to perform intelligent tasks.

Output 2

AI enables computers to simulate human intelligence.

Output 3

Artificial intelligence allows machines to learn and reason.

Illustrative outputs, not actual model responses.

### **3. Why is it set to 1 in your project?**

Because the notebook only needs one answer to test the fine-tuned Llama 2 model.

Returning multiple answers would consume additional computation without being necessary for this simple test.

**Remember the difference:**

* `<span>num_return_sequences=1</span>` → One complete response.
* `<span>max_length=200</span>` → Maximum total number of tokens in that sequence.

These two parameters control completely different things.

### **Interview-ready answer**

"`<span>num_return_sequences</span>` specifies the number of output sequences generated for a given input prompt. In this project, it is set to 1 because we only need one response."

### **Quick question**

If `<span>num_return_sequences=3</span>`, does the model generate three tokens or three complete responses?

A. Three tokens.

B. Three complete responses.

C. Three training datasets.

D. Three embeddings.



Let's understand this line step by step:

```
eos_token_id=tokenizer.eos_token_id,
```

### **1. First, what is EOS?**

EOS stands for **End Of Sequence**.

When an LLM generates a response, it produces tokens one by one.

For example:

```
Artificial → intelligence → enables → machines → to → learn → [EOS]
```

`<span>[EOS]</span>` is a special token that indicates that the generated sequence has ended.

### **2. What is **`<span>tokenizer.eos_token_id</span>`**?**

Let's break it into three parts:


| Component                   | Meaning                                           |
| --------------------------- | ------------------------------------------------- |
| `<span>tokenizer</span>`    | Converts text into tokens and tokens into text.   |
| `<span>eos_token</span>`    | Special token representing the end of a sequence. |
| `<span>eos_token_id</span>` | Numerical ID assigned to that special token.      |

Remember, models don't directly process ordinary words. Text is converted into tokens, and tokens are represented internally using numerical IDs.

For example, imagine:

```
tokenizer.eos_token = "</s>"
tokenizer.eos_token_id = 2
```

Here, `<span>2</span>` is just an illustrative ID, not a claim about your model's actual tokenizer.

### **3. What does the complete line do?**

```
eos_token_id=tokenizer.eos_token_id,
```

It tells the text-generation pipeline which token represents the end of a sequence.

When that stopping token is generated, the generation process can stop.

**Simple analogy:**

Imagine writing an answer in an examination.

* You start writing.
* You complete your answer.
* You put a full stop.

The EOS token works somewhat like that full stop: it signals that the sequence is complete.

### **4. Why do we need it?**

Without appropriate stopping conditions, a model might continue generating unnecessary text.

The EOS token helps the generation process recognize when to stop.

Note that generation can also stop because of `<span>max_length</span>` or other stopping conditions.

### **Interview-ready answer**

"`<span>eos_token_id</span>` specifies the numerical token ID representing the end of a sequence. It allows the generation pipeline to recognize when the model has generated its stopping token."

### **Quick question**

What does `<span>tokenizer.eos_token_id</span>` return?

A. The total number of tokens in the prompt.

B. The numerical ID of the end-of-sequence token.

C. The number of layers in Llama 2.

D. The number of generated responses.





Let's understand this line:

```
max_length=200,
```

### **1. What does **`<span>max_length</span>`** mean?**

It specifies the **maximum total number of tokens allowed in the input prompt plus the generated response**.

Remember, an LLM generates responses one token at a time.

For example, suppose:

* Your input prompt contains 20 tokens.
* `<span>max_length=200</span>`.

Then the model can generate approximately 180 additional tokens.

**Example: Maximum length = 200 tokens**

**Input prompt**

20 tokens

**Generated response**

Up to 180 tokens

**Maximum total**

# **200 tokens**

These numbers are illustrative. The model may stop earlier if it generates an EOS token.

### **2. Why do we use it?**

Suppose you ask:

"What is a large language model?"

Without a suitable generation limit, the model might generate a much longer response than you need.

By setting `<span>max_length=200</span>`, you limit the total sequence length.

### **3. What happens if we change the value?**


| Value                         | Effect                     |
| ----------------------------- | -------------------------- |
| `<span>max_length=50</span>`  | Shorter maximum sequence   |
| `<span>max_length=200</span>` | Longer maximum sequence    |
| `<span>max_length=500</span>` | Allows more generated text |

A larger value allows longer responses, but can increase generation time and memory requirements.

### **4. Important: **`<span>max_length</span>`** vs **`<span>max_new_tokens</span>`

These two are often confused in interviews.

* `<span>max_length=200</span>`: Maximum length of input + output combined.
* `<span>max_new_tokens=200</span>`: Maximum number of newly generated tokens, excluding the input prompt.

For new applications, `<span>max_new_tokens</span>` is often easier to reason about.

### **Interview-ready answer**

"`<span>max_length</span>` defines the maximum total token length of the generated sequence, including the input prompt. It controls how long the model's output can become."

### **Quick question**

Your input prompt contains 30 tokens, and you set `<span>max_length=200</span>`. Approximately how many tokens can the model generate?

A. 200

B. 230

C. 170

D. 30




This is the final part of your inference notebook. It takes the generated response and displays it.

```
for seq in sequences:
    print(seq['generated_text'])
```

Let's understand both lines.

## **1. First line**

```
for seq in sequences:
```

**What does this mean?**

Remember, earlier we wrote:

```
sequences = pipeline(...)
```

The pipeline generated the response and stored it in `<span>sequences</span>`.

Now we are using a `<span>for</span>` loop to go through the generated results one by one.

* `<span>sequences</span>` → Contains the generated output results.
* `<span>seq</span>` → Represents one result at a time.

For example, if `<span>num_return_sequences=3</span>`, the loop would process three results.

Since your project uses `<span>num_return_sequences=1</span>`, it normally processes one result.

## **2. Second line**

```
print(seq['generated_text'])
```

This displays the generated text.

Let's break it down:


| Component                         | Meaning                                           |
| --------------------------------- | ------------------------------------------------- |
| `<span>print()</span>`            | Displays something on the screen.                 |
| `<span>seq</span>`                | Current generated result.                         |
| `<span>['generated_text']</span>` | Accesses the generated-text field in that result. |

The pipeline returns a list of result dictionaries. Each dictionary contains a `<span>generated_text</span>` field.

For example, imagine the output looks like this:

```
[
    {
        'generated_text': 'What is a large language model? A large language model is an AI model trained on text data...'
    }
]
```

Then:

```
seq['generated_text']
```

extracts the text from that dictionary.

## **3. Complete inference workflow**

**Input prompt**

**Fine-tuned Llama 2 model**

Generates tokens

**sequences**

Stores generated results

**for seq in sequences**

Iterates through results

**print(seq['generated****\_****text'])**

Displays the response

## **4. Interview-ready explanation**

"The pipeline generates text and returns the results as a list of dictionaries. We iterate through this list and access the `<span>generated_text</span>` key to display the model's response."

## **Test your understanding**

**What is the purpose of **`<span>seq['generated_text']</span>`**?**

It trains the model.

It extracts the generated text from the result dictionary.

It loads the tokenizer.

It creates embeddings.

Check answer

**You have now completed the main inference workflow in **`<span>Fine_Tune_Model_Test.ipynb</span>`**.**

The next useful step is to understand the entire project from beginning to end and practise explaining it as you would in a GenAI placement interview.
