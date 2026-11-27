# **Interview Q&A — Scenario-Based: Large File Handling in an AI Application(Important)**

### **Scenario: Building an AI Lecture Summarization Application**

**Interviewer:** Suppose you are building an AI application where students upload lecture videos of 100 MB or more and ask the AI to summarize them, generate notes, and answer questions. How would you handle these large files efficiently?

**Answer:**

In this scenario, I would avoid sending the entire video file as raw payload in every API request because it would increase network overhead, latency, and resource consumption.

Instead, I would use a **Files API architecture**. First, I would upload the video once using the Files API. After the upload, I would receive a file ID or URI that references the uploaded video.

Whenever I need to process the video, I would pass that lightweight reference to the API instead of retransmitting the complete 100 MB file.

The workflow would be:

1. Student uploads a 100 MB lecture video.
2. The video is uploaded once through the Files API.
3. I receive a file ID or URI.
4. I pass the reference to the AI API for processing.
5. The model generates a transcript, summary, or notes.
6. I store the results and delete the uploaded file when no longer needed, according to the retention policy.

This approach makes the application more efficient, especially when the same video is used for multiple operations.

### **Q2. Interviewer: Why not directly send the 100 MB video in every API request?**

**Answer:**

If I send the entire video directly in every request, I would repeatedly transfer the same data even when I only need a different operation performed on it.

For example, a student might request:

* First, a summary.
* Then, important questions.
* Then, chapter-wise notes.
* Finally, answers to follow-up questions.

Sending the complete 100 MB video for all these requests would be wasteful. Instead, I would upload it once and reuse its file reference for subsequent requests, as long as the file remains available.

### **Q3. Interviewer: How would you manage the uploaded file after processing?**

**Answer:**

I would implement a file lifecycle management strategy.

Once the video is uploaded, it would remain available for the processing and follow-up operations required by the application. After the processing is complete and the student no longer needs access to the original file, I would delete it manually or allow the configured retention policy to expire.

For example, if the file retention period is 48 hours, I would ensure the application accounts for that expiration period. I would retain the generated summary and notes in my own database if they need to remain available longer.

### **Q4. Interviewer: What if the student wants to ask questions about the same video multiple times?**

**Answer:**

I would reuse the existing file reference rather than upload the video again, provided the reference is still valid and the API supports reuse.

For example, if the student initially requests a summary and later asks, *"Explain the second topic in more detail,"* I can use the existing file reference or previously generated transcript/context, rather than retransmitting the entire video.

This reduces redundant file transfers and improves efficiency.

### **Q5. Interviewer: What if the uploaded file expires after 48 hours, but the student wants to ask a question on the third day?**

**Answer:**

If the file reference has expired, I would no longer rely on that reference. I would design the application to preserve reusable outputs, such as transcripts, summaries, chapters, and extracted text, in my own storage.

If the original video is required again, the student would need to re-upload it unless I had retained it in authorized storage.

This is why file retention policies and application-level storage should be designed separately.

### **Q6. Interviewer: What is the main architectural decision you made in this scenario?**

**Answer:**

The main architectural decision is separating **file upload and storage from model inference**.

Instead of sending large media payloads repeatedly, I upload the file once, obtain its URI or file ID, and use that reference in subsequent operations.

This improves bandwidth efficiency, reduces repeated upload latency, and makes the application easier to scale.

## **Interview takeaway**

> **When handling large files in AI applications, I prefer uploading the file once through a Files API and passing its URI or file ID to subsequent requests, rather than repeatedly sending the raw file payload. I also implement lifecycle management, including retention, reuse, and deletion, to optimize performance, storage, and cost.**

This is a strong interview scenario because it connects API architecture with a real application—**AI lecture summarization**—rather than asking you to memorize what a URI or Files API is in isolation.
