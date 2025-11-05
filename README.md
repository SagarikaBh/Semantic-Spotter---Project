# Semantic-Spotter---Project
Semantic Spotter Project Submission
## 1. Background
This project showcases how to build a Retrieval-Augmented Generation (RAG) system tailored to the insurance domain using LangChain.

## 2. Problem Statement
The objective is to develop a reliable generative search system that can accurately respond to queries based on a collection of insurance policy documents.

## 3. Document
Access the policy documents here [here](./Policy+Documents)

## 4. Approach
LangChain is a powerful framework designed to streamline the development of applications powered by large language models (LLMs). It offers a rich set of tools, components, and interfaces that simplify the creation of LLM-driven solutions. LangChain supports integration with major model providers like OpenAI, Cohere, and Hugging Face.

Its modular and compositional architecture allows developers to build sophisticated applications in Python or JavaScript/TypeScript. LangChain facilitates external system connectivity, enabling access to necessary data for solving complex tasks. It includes abstractions for core functionalities and built-in integrations for reading and writing data, accelerating development.

LangChain is model-agnostic and supports continuous iteration across various LLMs, making it ideal for building customizable and scalable applications.

Key Elements of LangChain:
- **Components**: Modular abstractions for working with language models, with ready-to-use implementations. Usable independently or within the LangChain ecosystem.

- **Use-Case Specific Chains**: Pre-assembled configurations of components tailored to specific tasks. These chains offer a high-level interface and are easily customizable.

Core Building Blocks:
* Model I/O: Interfaces for LLMs and chat models, including prompts and output parsers.

* Retrieval: Tools for accessing domain-specific data (e.g., document loaders, transformers, embedding models, vector stores, retrievers).

* Chains: Sequences of LLM calls for structured workflows.

* Memory: Mechanisms to persist state across chain executions.

* Agents: Allow chains to select tools dynamically based on directives.

* Callbacks: Enable logging and streaming of intermediate steps.

## 5. System Layers
- **PDF Reading & Processing**: Utilize LangChain’s PyPDFDirectoryLoader to ingest and process PDFs from a specified directory.

- **Document Chunking**: Apply the RecursiveCharacterTextSplitter to segment text. This splitter prioritizes semantic coherence by splitting on characters like "\n\n", "\n", " ", and "", preserving paragraph and sentence integrity.

- **Embedding Generation**: Use OpenAIEmbeddings to convert text into vector representations. LangChain supports multiple embedding providers, enabling operations like similarity search and sentiment analysis. The base class includes methods for embedding both documents and queries.

- **Embedding Storage in ChromaDB**: Store embeddings using LangChain’s CacheBackedEmbeddings with ChromaDB as the backend.

- **Retrievers**: Implement retrievers to fetch documents based on unstructured queries. Unlike vector stores, retrievers focus solely on returning relevant documents. The VectorStoreRetriever is widely supported and commonly used.

- **Cross-Encoder Re-Ranking**: Enhance semantic search results by re-ranking with a cross-encoder. Each query-response pair is scored for relevance using HuggingFaceCrossEncoder with the model BAAI/bge-reranker-base.

- **Chains**: Combine multiple components into cohesive workflows using LangChain’s chain functionality. For instance, a chain can format user input with a PromptTemplate and pass it to an LLM. More complex chains can be built by nesting or integrating with other components. This project uses the prompt rlm/rag-promp from LangChain Hub within a RAG chain.

## 6. System Architecture
![](arch1.png)
![](arch2.png)

## 7. Prerequisites
- Python version 3.7 or higher

- LangChain version 0.3.13

- Add your OpenAI API key to the file named OpenAI_API_Key.txt to enable API access.

## 8. Running the Project
- Clone the GitHub repository:

 bash
git clone https://github.com/SagarikaBh/Semantic-Spotter---Project.git
- Open the Jupyter notebook and execute all cells sequentially.
