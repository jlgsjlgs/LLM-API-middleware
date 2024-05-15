# Overview

This repository contains two Python files that serve specific purposes within the AI Chatbot application:

1. **Backend Microservice Server:** This file acts as a middleware between a frontend and a Large Language Model (LLM) API. It is built using Python and the LangChain framework, utilizing Flask to serve the API. The server facilitates communication between the user interface and the language model, enabling the system to provide responses to user queries based on provided context.

2. **Embedding Script:** This script is responsible for preprocessing documents, chunking them, converting the chunks into embeddings using an embedding API, and storing these embeddings in a vector store (Azure CosmosDB). It handles various document formats such as PDF and DOCX, preprocesses them accordingly, and stores the embeddings for later retrieval.

---

## LLM API Middleware

#### Requirements
- Python
- Flask
- LangChain

#### Usage
1. Install the required packages by running `pip install -r requirements.txt`.
2. Set up environment variables by creating a `.env` file in the `config` directory and specifying the required variables (e.g. OpenAI API Key).
3. Run the server using `python3 server.py`.
4. Interact with the server through the specified API endpoints.

#### API Endpoint
- `/getAns`: POST endpoint for receiving user queries and returning responses based on context and chat history.



**Method**: POST
**Content Type**: application/json
**Payload**:
  - `userInput` (string): User query or input.
  - `chatHistory` (list of strings): History of chat messages (optional).

**Response**:
  - `Answer` (string): Response to the user query.

---

## Embedding Script

#### Requirements
- Python
- LangChain
- pymongo

#### Usage
1. Install the required packages by running `pip install -r requirements.txt`.
2. Set up environment variables by creating a `.env` file in the `config` directory and specifying the required variables (e.g. MONGO_URI).
3. Place the documents to be embedded in the `data` directory.
4. Run the script using `python3 embedder.py`.
5. Embeddings will be generated for the documents and stored in the specified Azure CosmosDB collection.

#### Functions
- `CosmosEmbedder`: Embeds documents from the `data` directory, stores the embeddings in Azure CosmosDB, and creates an index for similarity search.
- `checkCosmos`: Prints all documents stored in the specified Azure CosmosDB collection.
- `deleteCosmos`: Deletes all documents from the specified Azure CosmosDB collection.
- `fetchCosmos`: Performs a similarity search query against the stored documents in Azure CosmosDB.

---

