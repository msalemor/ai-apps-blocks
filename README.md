# AI-Infused Appplications with Azure OpenAI<br/>Application Development Building Blocks


## OpenAI fundamentals

### What are the models and what models are there (ADA, GPT 3.5, 4)?

Azure OpenAI offers several models including GPT for text generation and ADA for embedings. These are REST endpoints hosted in Azure that are generally executed by making a POST request to the endpoint. Models may offer different token sizes, tokens per minute, and performance. To call these endpoints, you will need to either get an API key or setup some other security mechanism in Azure.

### What are tokens?

A token is defined as 3/4 of a word in English. In other languages that have accents and other characters, those characters count as tokens. If you want to see the effect of tokes, OpenAI offers a tokenizer tool at: https://platform.openai.com/tokenizer.

### What are the token limits and why are they important?

Models like GPT 3.5, 4, and ADA have different token count limitations. It is important to understand these limits to be able to optimize the number of requests an account can handle. Three factors are most important in knowing the token limitations including context size, throttling, and cost. Context size is the maxium amount of tokens a model supports. Some models support 4K, 8K, 16K, 32K, and 128K. Throttling occurs when limitations are exceeded. In Azure, there are two limitations, tokens per minute, and requests per minute. If you exceed any of these limitations, Azure with throttle the respose returning an HttpStatus code 429 or Too Many Requests. As far as cost, different models different cost depending on the model.

[Azure OpenAI Service pricing](https://azure.microsoft.com/en-us/pricing/details/cognitive-services/openai-service/)

### What are prompts and completions?

### What is Prompt engineering?
 
### What is the difference between an LLM vs Chat model?

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
