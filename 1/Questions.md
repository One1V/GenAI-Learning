1> If Trannsformers and Accelerate are librarires then what is SAutoTokeizer.

2>Teach me parameters which i will use in pipeline across projects how and when to use them and how many means how to know that what combination is required?

3>Bappy inn this project has used a model which is deplyed by himself or can say that he redeployed lama model is it important for me to know how to deploy own model on hugging face , and all aspects around that.

4>What is the flow (teach universal flow).

5>How actual developers see the mdoels to intergrate or wwhere they do read or research from.

6>What is the difference between fine-tuning and inference?

7>What is Hugging Face Transformers?

8> What is the purpose of `AutoTokenizer`?



These are the most likely questions.

1. What is the purpose of this notebook?
2. What is the difference between fine-tuning and inference?
3. Which pre-trained model are you using?
4. What is Hugging Face Transformers?
5. What is the purpose of `AutoTokenizer`?
6. What is a text-generation pipeline?
7. How do you load a fine-tuned model?
8. How do you pass a custom prompt to Llama 2?
9. What is the purpose of the `[INST]` and `[/INST]` tokens?
10. How do you generate multiple responses from an LLM?


### **B. Model loading and hardware questions**

1. Why do we use `torch.float16` instead of `torch.float32`?
2. What is `device_map="auto"`?
3. What is the role of Accelerate?
4. Why does loading a 7-billion-parameter model require significant GPU memory?
5. What is the difference between CPU and GPU inference?
6. What happens if the model doesn't fit into GPU memory?

### **C. Text generation parameters**

These are particularly important for GenAI interviews.

1. What is `do_sample=True`?
2. What is `top_k` sampling?
3. What is `temperature`?
4. What is `top_p`?
5. What is `max_length`?
6. What is `eos_token_id`?
7. What is `num_return_sequences`?
8. What happens if you increase the number of generated tokens?
9. What is the difference between greedy decoding and sampling?

### **D. Practical implementation questions**

An interviewer might ask you to modify the notebook.

1. How would you change the prompt?
2. How would you generate three responses instead of one?
3. How would you control the length of the generated response?
4. How would you use another fine-tuned model?
5. How would you load a model using 4-bit quantization?
6. How would you integrate this model into a FastAPI application?

Difference bw llm and model.

I have heard something like using two types of pip ! and maybe # what are they  and how are they differenta nd when to use which one?

What are the common things we need to intsall with pip in projects commonly meanshow many are there and what are they which i must need to know.

What does pip install means

Which model to prefer for what task like is there any thing like llama do better with text and gemini with image or so?

What happens exactly when we fine tune a model a new model gets generated , or that model is used with extra constraints or that previous one make a new one ....


**Interview questions:**

1. What is tokenization?
2. Why can't an LLM directly process ordinary text?
3. What is the difference between a token and a token ID?
4. What is the purpose of AutoTokenizer?

Ques -> What is Auto Class.


### **4. Interview questions**

1. What is a Hugging Face pipeline?
2. Why do we use pipelines instead of implementing everything manually?
3. What are different types of pipelines?
4. What is the difference between a pipeline and a model?
5. Can we use pipelines for image classification?

### **4. Interview questions**

1. What is a prompt in Generative AI?
2. What is prompt engineering?
3. What is the difference between a prompt and a training dataset?
4. What is zero-shot prompting?
5. What is few-shot prompting?
6. What makes a good prompt?
