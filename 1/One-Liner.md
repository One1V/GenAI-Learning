| Skill                    | What they want to evaluate                    |
| ------------------------ | --------------------------------------------- |
| Transformers             | Understanding of Hugging Face                 |
| Tokenization             | Understanding of text-to-token conversion     |
| Model loading            | Ability to load an existing LLM               |
| Inference                | Ability to generate responses                 |
| Sampling                 | Understanding of generation control           |
| PyTorch                  | Basic tensor precision and hardware knowledge |
| Practical implementation | Ability to modify existing code               |

Fine-tuning = Taking an already pre-trained model and training it further on a specific dataset so that it adapts its learned parameters to a particular task or domain.

"Fine-tuning is the process of taking a pre-trained model and further training it on a task-specific dataset to adapt its weights and improve its performance on that particular task."

* **Pre-training:** Teaching a model general language patterns using large datasets.
* **Fine-tuning:** Further training an existing model on a specific dataset or task.
* **Inference:** Giving the trained model an input and getting its output.


* `transformers`: Hugging Face library that provides pre-trained models, tokenizers and pipelines.
* `accelerate`: Helps execute models efficiently across available hardware (GPU, CPU or multiple GPUs).

**What is AutoTokenizer?**

Before an LLM can understand our input, text needs to be converted into tokens and then into numerical token IDs.


#### import torch

Imports **PyTorch**, a deep learning framework.

Why do we need it?

Our Llama 2 model is a neural network. PyTorch provides the tensor operations and computational infrastructure needed to execute it.


**1. What does this line do?**

tokenizer = AutoTokenizer.from_pretrained(model)

* `AutoTokenizer`: Hugging Face class responsible for loading the appropriate tokenizer.
* `from_pretrained(model)`: Loads the tokenizer configuration and vocabulary associated with the specified model.
* `tokenizer`: Variable that stores the loaded tokenizer object
* What happens internally?

1. Hugging Face identifies the model repository.
2. It retrieves the tokenizer files and configuration.
3. It initializes the tokenizer.
4. We can now convert text into token IDs and decode token IDs back into text.
