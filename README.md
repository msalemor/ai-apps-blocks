# AI-Infused Appplications with Azure OpenAI<br/>Application Development Building Blocks


## OpenAI fundamentals

### What are the models and what models are there (ADA, GPT 3.5, 4)?

Azure OpenAI offers several models including GPT for text generation and ADA for embedings. These are REST endpoints hosted in Azure that are generally executed by making a POST request to the endpoint. Models may offer different token sizes, tokens per minute, and performance. To call these endpoints, you will need to either get an API key or setup some other security mechanism in Azure.

### What are tokens?

A token is defined as 3/4 of a word in English. In other languages that have accents and other characters, those characters count as tokens. If you want to see the effect of tokes, OpenAI offers a tokenizer tool at: https://platform.openai.com/tokenizer.

### What are the token limits and why are they important?

Models like GPT 3.5, 4, and ADA have different token count limitations. It is important to understand these limits to be able to optimize the number of requests an account can handle. Three factors are most important in knowing the token limitations including context size, throttling, and cost. Context size is the maximum amount of tokens a model supports. Some models support 4K, 8K, 16K, 32K, and 128K. Throttling occurs when limitations are exceeded. In Azure, there are two limitations, tokens per minute, and requests per minute. If you exceed any of these limitations, Azure with throttle the respose returning an HttpStatus code 429 or Too Many Requests. As far as cost, different models have different costs. The current models and pricing can be found here: [Azure OpenAI Service pricing](https://azure.microsoft.com/en-us/pricing/details/cognitive-services/openai-service/)

### What are prompts and completions?

When a post request is sent to a GPT model, this is called a prompt. There response coming back from a GPT model is called a completion. To make a prompt request, several parameters need to be passed including, for example, the messages, the temperature, the maximum response prompts, etc. The completion is also more than just an answer, it can include things like information about the model, the tokens, and the actual response message. Here's the current API reference that lists all the available parameters for making these POST REST calls: https://learn.microsoft.com/en-us/azure/ai-services/openai/reference. The response can be received all at once or stream. A response can receive an error message, this happens most often when a response is longer than the desired token count set in the max_tokens payload.

### What is prompt engineering?

Wikipedia defined [prompt engineering](https://en.wikipedia.org/wiki/Prompt_engineering) as "Prompt engineering is the process of structuring text that can be interpreted and understood by a generative AI model.[1][2] A prompt is natural language text describing the task that an AI should perform."

A good playground is a useful starting point for your development. You can experiment with different prompts until you achieve the results you want, and then create templates from your prompts. GPT models are versatile models that can handle various tasks such as summarization, analysis, classification, language translation, and more. You can use a single prompt to do all these tasks, but you can also divide the tasks into smaller units and combine them to create more complex interactions. For more information on prompt engineering, you can read this article: https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/prompt-engineering.

Once you are satisfied with your prompt, think about how the application will come together. Do you have an ingestion phase, what will you do with the output, etc.

### What is the difference between an LLM vs Chat model?

### Where is the difficulty? ("The everything else")

Making a call to a prompt is as simple as sending one sentence via a CURL command to GPT. Even just this one simple action can yield amazing results. So if it is so simple to consume a GPT endpoint, where is the difficulty? It is the "everything else".

- Ingestion (data source, data format, extracting text)
- Prompt engineering
- Processing the completions
- Fault handling and resiliency
- The frontend

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
