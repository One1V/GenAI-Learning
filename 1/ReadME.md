So we are actually learning by using a project.

We are evaluating the code and finding how can we reproduce it for other projects.


**1. **`Fine_tune_Llama_2.ipynb`** — Fine-tuning**

Here, the pretrained Llama 2 model is trained further using the Guanaco dataset.

* Loads the pretrained model.
* Prepares the dataset.
* Applies LoRA/QLoRA.
* Trains the model using `<span>SFTTrainer</span>`.
* Saves the trained adapter.
* Merges and uploads the model.

Training happens here

### **2. **Fine_Tune_Model_Test.ipynb`** — Inference**

Your current code:

```
pipeline = transformers.pipeline(    "text-generation",    model=model,    torch_dtype=torch.float16,    device_map="auto")
```

It:

* Loads the already fine-tuned model from Hugging Face.
* Loads it in FP16 precision.
* Automatically assigns model components to available hardware.
* Creates a pipeline to generate text.

Inference preparation happens here

### **Overall workflow**

**Pretrained Llama 2**

**Fine-tuning using Guanaco dataset**

Notebook 1

**Fine-tuned model saved on Hugging Face Hub**

**Load model using pipeline()**

Notebook 2 — Your current code

Inference

**Interview question:** What is the difference between training and inference?

* Training: Updating model parameters using training data.
* Inference: Using an already-trained model to generate predictions or responses.
