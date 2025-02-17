
# Document Q&A Bot with RAG

This project is a **Retrieval-Augmented Generation (RAG)** system that allows users to query documents using natural language. It processes PDFs, creates a vector store for semantic search, and uses a reasoning model to generate answers based on the retrieved context. The system is accessible via a Streamlit web interface.

## Features

- **PDF Ingestion**: Automatically processes PDFs from a specified directory and splits them into chunks for efficient retrieval.
- **Semantic Search**: Uses a vector store (Chroma) with HuggingFace embeddings to retrieve the most relevant document chunks based on user queries.
- **Reasoning Model**: Generates concise and accurate answers using a reasoning model (e.g., OpenAI or HuggingFace) based on the retrieved context.
- **Streamlit Interface**: Provides a user-friendly web interface for interacting with the system.

## Files Overview

- **`ingest_pdfs.py`**: 
  - Loads PDFs from a directory, splits them into chunks, and creates a vector store using Chroma and HuggingFace embeddings.
  
- **`openai_rag.py`**:
  - Implements the RAG pipeline using OpenAI's API for the reasoning model and HuggingFace for the tool model.
  - Provides a `rag_with_reasoner` tool that retrieves relevant document chunks and generates answers using the reasoning model.

- **`r1_smolagent_rag.py`**:
  - Similar to `openai_rag.py`, but allows switching between HuggingFace and local models (e.g., Ollama) for the reasoning model.
  - Implements the RAG pipeline with a focus on flexibility in model selection.

- **`streamlit.py`**:
  - Provides a Streamlit-based web interface for users to interact with the RAG system.
  - Displays chat history, handles user input, and generates responses using the primary agent.

## Setup

### Prerequisites

- Python 3.8 or higher
- [Poetry](https://python-poetry.org/) (optional, for dependency management)
- OpenAI API key (if using OpenAI models)
- HuggingFace API token (if using HuggingFace models)

### Installation

1. Clone the repository:
   
   git clone https://github.com/abhishekabhi779/R1qwenRag
   cd rag
   

2. Install dependencies:
   
   pip install -r requirements.txt


3. Set up environment variables:
   - Create a `.env` file in the root directory and add the following:
    
     REASONING_MODEL_ID=your-reasoning-model-id
     TOOL_MODEL_ID=your-tool-model-id
     HUGGINGFACE_API_TOKEN=your-huggingface-token
     OPENAI_API_KEY=your-openai-api-key
  

### Usage

1. **Ingest PDFs**:
   - Place your PDFs in the `data` directory.
   - Run the following command to process the PDFs and create the vector store:
     
     python ingest_pdfs.py
     

2. **Run the Streamlit Interface**:
   - Start the Streamlit app:
     
     streamlit run streamlit.py
     
   - Open your browser and navigate to the provided URL to interact with the bot.

3. **Ask Questions**:
   - Use the chat interface to ask questions about the documents. The bot will retrieve relevant information and generate answers based on the context.

## Configuration

- **Model Selection**:
  - You can switch between HuggingFace and local models by setting the `USE_HUGGINGFACE` environment variable in the `.env` file.
  - Example:
   
    USE_HUGGINGFACE=no  # Use local models (e.g., Ollama)
    

- **Chunk Size and Overlap**:
  - Modify the `chunk_size` and `chunk_overlap` parameters in `ingest_pdfs.py` to adjust how PDFs are split into chunks.

## Contributing

Contributions are welcome! If you have any suggestions, bug reports, or feature requests, please open an issue or submit a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.


