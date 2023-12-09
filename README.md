# AI-Infused Appplications with Azure OpenAI<br/>Application Development Building Blocks


## OpenAI fundamentals

### What are the models and what models are there (ADA, GPT 3.5, 4)?

Azure OpenAI provides various models for different tasks, such as GPT for text generation and ADA for embeddings. These models are accessible through REST endpoints hosted on Azure, which can be invoked by sending a POST request to the corresponding URL. The models may differ in their token sizes, tokens per minute, and performance. To access these endpoints, you will need to obtain an API key or configure another security mechanism on Azure.

### What are tokens?

A token is defined as 3/4 of a word in English. In other languages that have accents and other characters, those characters count as tokens. If you want to see the effect of tokes, OpenAI offers a tokenizer tool at: https://platform.openai.com/tokenizer.

### What are the token limits and why are they important?

Models like GPT 3.5, 4, and ADA have different token count limitations. It is important to understand these limits to be able to optimize the number of requests an account can handle. Three factors are most important in knowing the token limitations including context size, throttling, and cost. Context size is the maximum amount of tokens a model supports. Some models support 4K, 8K, 16K, 32K, and 128K. Throttling occurs when limitations are exceeded. In Azure, there are two limitations, tokens per minute, and requests per minute. If you exceed any of these limitations, Azure with throttle the respose returning an HttpStatus code 429 or Too Many Requests. As far as cost, different models have different costs. The current models and pricing can be found here: [Azure OpenAI Service pricing](https://azure.microsoft.com/en-us/pricing/details/cognitive-services/openai-service/)

### What are prompts and completions?

When a post request is sent to a GPT model, this is called a prompt. There response coming back from a GPT model is called a completion. To make a prompt request, several parameters need to be passed including, for example, the messages, the temperature, the maximum response prompts, etc. The completion is also more than just an answer, it can include things like information about the model, the tokens, and the actual response message. Here's the current API reference that lists all the available parameters for making these POST REST calls: https://learn.microsoft.com/en-us/azure/ai-services/openai/reference. The response can be received all at once or stream. A response can receive an error message, this happens most often when a response is longer than the desired token count set in the max_tokens payload.

### What is prompt engineering?

Wikipedia defined [prompt engineering](https://en.wikipedia.org/wiki/Prompt_engineering) as "Prompt engineering is the process of structuring text that can be interpreted and understood by a generative AI model. A prompt is natural language text describing the task that an AI should perform."

A good playground is a useful starting point for your development. You can experiment with different prompts until you achieve the results you want, and then create templates from your prompts. GPT models are versatile models that can handle various tasks such as summarization, analysis, classification, language translation, and more. You can use a single prompt to do all these tasks, but you can also divide the tasks into smaller units and combine them to create more complex interactions. For more information on prompt engineering, you can read this article: https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/prompt-engineering.

Once you are satisfied with your prompt, think about how the application will come together. Do you have an ingestion phase, what will you do with the output, etc?

### What is the difference between an LLM vs a Chat model?

A GPT model can maintain a record of the previous interactions with the user. These are called messages. The chat model and the LLM model differ in how they use the messages. The chat model incorporates the messages into its output, while the LLM model generates a completion based on the user's prompt without considering the messages (answer/response).

### What are embeddings?

An embedding is a vector (an array) representation of a text. OpenAI offers ADA-002 as the embedding model. In the resource-augemented-generation pattern, for example, text files and broken into chunks, the chunks are sent to ADA for embedding and stored in a vector database. When a user submits a query, the query is itself embedded and then compared against the embedded chunks in the vector database. Using something called cosine similarity, results are ranked by the closest distance to the query.

### Where is the difficulty? ("The everything else")

Making a call to GPT endpoint is as simple as sending one sentence via a CURL command like this: 

```bash
curl https://YOUR_RESOURCE_NAME.openai.azure.com/openai/deployments/YOUR_DEPLOYMENT_NAME/chat/completions?api-version=2023-05-15 \
  -H "Content-Type: application/json" \
  -H "api-key: YOUR_API_KEY" \
  -d '{"messages":[{"role": "user", "content": "What is the speed of light?"}]}'
```

Even just this one simple action can yield amazing results. So if it is so simple to consume a GPT endpoint, where is the difficulty? It is the "everything else".

- Selecting the right model
- Ingestion
- Prompt engineering
- Processing the completions
- Fault handling and resiliency
- Security and Responsible AI
- Creating and storing embeddings
- Selecting a Vector database, 
- Retrieving and consuming results from a vector database
- The user experience (frontend)

## Application architecture fundamentals

Writing an AI-infused application is no different than planning a regular application. You need to consider the usual layers like validation, scalability, resiliency, data access, security, etc. Since OpenAI are REST endpoint, particularly feeling comfortable with the following concepts is important.

-	Making REST requests (POST)
-	Configuring HttpClient
-	Configuring retry logic

## SDKs and Orchestrators

-	OpenAI SDK
-	LangChain
- 	Semantic Kernel

## RAG Pattern

- Ingestion
- Text chunking
- Embeddings (ADA: How can a 1500, 8K tokens)
- Vector Databases
- Recalling embeddings
- Cosine similarity
- Grounding
- Tabular data (CSVs, SQL)

## Vector Database (Azure Cognitive Search)

- Different search options
