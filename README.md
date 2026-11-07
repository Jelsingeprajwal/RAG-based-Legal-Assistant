# RAG-based Legal Assistant Chatbot

A powerful, context-aware legal assistant chatbot built with **LangChain** and advanced **Retrieval-Augmented Generation (RAG)** techniques.

The application combines **dense and sparse retrieval** by leveraging traditional **BM25-based keyword search** alongside **semantic vector search**, ensuring both lexical precision and deep contextual relevance. It intelligently analyzes the complexity of each user query and dynamically selects the most appropriate retrieval strategy.

For complex reasoning tasks, the system employs **Multi-Hop retrieval** across multiple documents, while **Multi-Query retrieval** is used as a semantic query expansion technique to improve recall and coverage. Results from these retrieval strategies are consolidated using **Reciprocal Rank Fusion (RRF)**, ensuring that the most contextually relevant documents are prioritized and passed to the language model as grounding context for response generation.

Additionally, the application includes a **custom-built chat history management module**, developed as a robust replacement for LangChain’s deprecated `ConversationSummaryBufferMemory`. This module reliably maintains conversational context across interactions without relying on unstable or deprecated abstractions.

## Features

- **PDF Document Processing**: Automatically processes and indexes legal PDF documents
- **Sparse (BM25) Retriever**: keyword-based retrieval method that ranks documents using term frequency and inverse document frequency to capture exact lexical matches between the query and documents
- **Dense Retriever**: FAISS-backed vector retriever with the `all-MiniLM-L6-v2` sentence transformer embedding model to perform semantic similarity search, retrieving documents based on contextual meaning rather than exact keyword matches
- **Multi-Query Retrieval**: Semantic query expansion strategy that generates multiple paraphrased or reformulated queries from the original user input to improve retrieval recall and coverage.
- **Multi-Hop Retrieval**: Decomposes a complex query into intermediate steps, retrieving and chaining context from multiple documents to enable reasoning across dispersed information sources
- **Reciprocal Rank Fusion (RRF)**: Merges results from multiple retrieval methods by prioritizing documents that consistently rank highly across different retrievers
- **Intelligent Query Classification**: Determines whether document retrieval is needed based on the complexity inferred
- **Conversation History Awareness**: Maintains conversation context across multiple turns
- **Vector Database Storage**: Efficiently stores and retrieves document embeddings using FAISS
- **Command-Line Interface**: Interactive terminal-based chat interface
- **Responsible AI Disclaimers**: Clearly communicates that responses are not substitutes for legal advice

## Technical Stack

- **Framework**: LangChain
- **Interface**: Command-line terminal interface
- **Embeddings**: HuggingFace (all-MiniLM-L6-v2)
- **Chat Model**: Cohere (command-r model)
- **Vector Store**: FAISS
- **Document Processing**: LangChain's PyPDFLoader
- **Text Splitting**: LangChain's RecursiveCharacterTextSplitter
- **Evaluation**: RAGAS
- **Traceability**: LangSmith
