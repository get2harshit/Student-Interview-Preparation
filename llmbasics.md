### 1. What is an LLM?

**LLM = Large Language Model**

- **Large** = trained on massive datasets
- **Language** = works with text and tokens
- **Model** = learns patterns from data
- **Purpose** = predict the next token based on context

---

### 2. How does an LLM generate text?

**LLM = predict next token repeatedly**

- **Input** = prompt converted into tokens
- **Token** = small unit of text
- **Prediction** = model calculates next-token probabilities
- **Generation** = selected token is added to context
- **Repeat** = continues until generation ends

---

### 3. What is a token?

**Token = basic unit processed by LLM**

- **Word** = can be one or multiple tokens
- **Example** = `"playing"` may become multiple tokens
- **Input tokens** = prompt
- **Output tokens** = generated response
- **Token count** = affects cost and context usage

---

### 4. What is a context window?

**Context window = maximum tokens model can process at once**

- **Contains** = input + conversation + output
- **Larger window** = more information available
- **Limitation** = cannot process unlimited context
- **Example** = documents may need chunking

---

### 5. What is a Transformer?

**Transformer = neural network architecture behind modern LLMs**

- **Core idea** = process relationships between tokens
- **Attention** = determines which tokens matter
- **Parallel processing** = processes input tokens efficiently
- **Foundation** = GPT, Llama, Claude-style models

---

### 6. What is attention?

**Attention = determines which tokens are relevant to each other**

- **Query** = what token is looking for
- **Key** = what token offers
- **Value** = information being retrieved
- **Attention score** = relevance between tokens
- **Self-attention** = tokens attend to other input tokens

---

### 7. What is self-attention?

**Self-attention = tokens attend to other tokens in same input**

- **Purpose** = understand contextual relationships
- **Example** = resolve what `"it"` refers to
- **Benefit** = captures long-range relationships
- **Used in** = Transformer architecture

---

### 8. What is an embedding?

**Embedding = numerical representation of meaning**

- **Input** = text
- **Output** = vector (list of numbers)
- **Similar meaning** = similar vector representation
- **Used for** = search, recommendations, RAG

---

### 9. What is the difference between embeddings and LLMs?

**Embedding model = represents meaning, LLM = generates content**

- **Embedding** = converts text into vectors
- **LLM** = generates tokens
- **Embedding** = useful for similarity search
- **LLM** = useful for generation and reasoning

---

### 10. What is pre-training?

**Pre-training = teaching model general language patterns**

- **Data** = large text datasets
- **Task** = predict missing/next tokens
- **Learning** = model adjusts parameters
- **Output** = general-purpose language model

---

### 11. What are parameters in an LLM?

**Parameters = learned numerical values of the model**

- **Learned** = during training
- **Represent** = learned patterns
- **More parameters** = potentially more capacity
- **Trade-off** = higher compute and memory requirements

---

### 12. What is fine-tuning?

**Fine-tuning = training an existing model on specific data**

- **Base model** = already pretrained
- **Dataset** = task-specific examples
- **Purpose** = adapt model behavior
- **Example** = customer-support response style

---

### 13. Fine-tuning vs prompting?

**Prompting = change input, fine-tuning = change model**

- **Prompting** = no model weight changes
- **Fine-tuning** = updates model parameters
- **Prompting** = easier and cheaper
- **Fine-tuning** = useful for consistent specialized behavior

---

### 14. What is instruction tuning?

**Instruction tuning = training model to follow instructions**

- **Training data** = instruction + expected response
- **Purpose** = improve instruction following
- **Example** = summarize, classify, extract
- **Result** = better task-oriented behavior

---

### 15. What is RLHF?

**RLHF = Reinforcement Learning from Human Feedback**

- **Human feedback** = humans compare model responses
- **Reward model** = learns preferred responses
- **Reinforcement learning** = optimizes model behavior
- **Purpose** = improve helpfulness and alignment

---

### 16. What is inference?

**Inference = using trained model to generate output**

- **Input** = prompt
- **Model** = trained parameters
- **Output** = generated tokens
- **Cost** = primarily compute + token usage

---

### 17. What is temperature?

**Temperature = controls randomness in token selection**

- **Low temperature** = more predictable output
- **High temperature** = more diverse output
- **0-ish** = deterministic-like behavior
- **Use low** = factual/structured tasks
- **Use higher** = creative generation

---

### 18. What is top-k sampling?

**Top-k = choose next token from top K candidates**

- **K** = number of candidates
- **Small K** = more restricted generation
- **Large K** = more possible choices
- **Purpose** = control generation randomness

---

### 19. What is top-p sampling?

**Top-p = choose tokens within probability mass P**

- **P** = cumulative probability threshold
- **Lower P** = fewer candidate tokens
- **Higher P** = more candidate tokens
- **Purpose** = control generation diversity

---

### 20. What is hallucination?

**Hallucination = model generates incorrect information confidently**

- **Cause** = model predicts plausible text, not guaranteed truth
- **Example** = fabricated citation
- **Risk** = high in factual applications
- **Mitigation** = RAG, validation, tool calls, structured outputs

---

### 21. How do you reduce hallucinations?

**Hallucination reduction = ground + constrain + verify**

- **Grounding** = provide trusted information
- **RAG** = retrieve relevant documents
- **Tools** = fetch real-time information
- **Structured output** = constrain response format
- **Validation** = verify generated results

---

### 22. What is RAG?

**RAG = Retrieval-Augmented Generation**

- **Retrieval** = find relevant information
- **Augmented** = add retrieved information to prompt
- **Generation** = LLM generates answer
- **Purpose** = answer using external knowledge

---

### 23. How does RAG work?

**RAG = chunk → embed → retrieve → generate**

- **Chunking** = split documents into smaller pieces
- **Embedding** = convert chunks into vectors
- **Retrieval** = find relevant chunks
- **Prompt** = provide chunks to LLM
- **Generation** = generate grounded answer

---

### 24. Why do we need embeddings in RAG?

**Embeddings = enable semantic similarity search**

- **Document** = converted into vector
- **Query** = converted into vector
- **Similarity** = compare vectors
- **Retrieval** = return semantically relevant chunks

---

### 25. What is a vector database?

**Vector database = stores and searches embeddings**

- **Vector** = numerical representation
- **Index** = enables efficient similarity search
- **Query** = finds nearby vectors
- **Examples** = Pinecone, Weaviate, Qdrant, pgvector

---

### 26. What is chunking in RAG?

**Chunking = splitting documents into retrievable pieces**

- **Small chunks** = precise retrieval
- **Large chunks** = more context
- **Overlap** = preserves context between chunks
- **Trade-off** = retrieval precision vs context

---

### 27. What is semantic search?

**Semantic search = search based on meaning**

- **Traditional search** = keyword matching
- **Semantic search** = meaning similarity
- **Embedding** = represents query meaning
- **Vector search** = finds similar content

---

### 28. What is prompt engineering?

**Prompt engineering = designing input to guide model behavior**

- **Instruction** = what model should do
- **Context** = information model should use
- **Constraints** = what model should avoid
- **Output format** = expected response structure

---

### 29. What is zero-shot prompting?

**Zero-shot = task without examples**

- **Instruction** = describe task
- **Examples** = none
- **Use** = straightforward tasks
- **Example** = `"Classify this review as positive or negative"`

---

### 30. What is few-shot prompting?

**Few-shot = task with a few examples**

- **Examples** = demonstrate expected behavior
- **Input** = new unseen example
- **Purpose** = guide model pattern
- **Benefit** = improves consistency for some tasks

---

### 31. What is function calling/tool calling?

**Tool calling = LLM requests an external function**

- **LLM** = decides which tool is needed
- **Tool** = executes actual operation
- **Result** = returned to LLM
- **Example** = database query, weather API, payment service

---

### 32. Why do LLM applications need tools?

**Tools = give LLM capabilities beyond text generation**

- **Database** = retrieve application data
- **API** = access external systems
- **Calculator** = perform precise calculations
- **Search** = retrieve current information
- **LLM** = decides when to use them

---

### 33. What is structured output?

**Structured output = model response follows defined schema**

- **Schema** = expected data structure
- **Example** = JSON object
- **Benefit** = easier application integration
- **Validation** = application can verify response

---

### 34. What is an AI agent?

**Agent = LLM-driven system that can plan and use tools**

- **LLM** = reasoning/generation engine
- **Tools** = external capabilities
- **Memory** = stores relevant information
- **Loop** = observe → decide → act → observe
- **Goal** = complete a task autonomously

---

### 35. LLM vs traditional ML?

**LLM = general-purpose language model, traditional ML = usually task-specific model**

- **LLM** = pretrained on massive text
- **Traditional ML** = often trained for specific prediction
- **LLM** = can perform multiple language tasks
- **Traditional ML** = commonly requires task-specific training

---

### 36. LLM vs chatbot?

**LLM = model, chatbot = application using the model**

- **LLM** = generates language
- **Chatbot** = product/interface around LLM
- **Chatbot** = can include memory, tools, RAG
- **Example** = customer-support chatbot using an LLM

---

### 37. What is model quantization?

**Quantization = reducing numerical precision of model weights**

- **FP16** = 16-bit floating point
- **INT8** = 8-bit integer
- **Benefit** = lower memory usage
- **Trade-off** = possible quality loss
- **Use** = running large models on limited hardware

---

### 38. What is inference latency?

**Inference latency = time taken to generate a response**

- **TTFT** = time to first token
- **Generation time** = time producing remaining tokens
- **Factors** = model size, hardware, prompt length
- **Optimization** = quantization, batching, caching

---

### 39. What is token throughput?

**Token throughput = tokens generated per unit time**

- **Metric** = tokens/second
- **Higher throughput** = more requests handled
- **Affected by** = model, hardware, batching
- **Useful for** = capacity planning

---

### 40. How would you build a production LLM application?

**Production LLM system = API + LLM + data + safety + observability**

```
Client
   ↓
API Service
   ↓
LLM Orchestrator
   ├── RAG → Vector DB
   ├── Tools → External Services
   └── LLM → Model Provider
   ↓
Response
```

- **API Service** = authentication + rate limiting
- **Orchestrator** = controls LLM workflow
- **RAG** = provides application knowledge
- **Tools** = access external systems
- **Observability** = logs, latency, token usage, errors
