# Retrieval-based QA System with PDF Input

This project implements a question-answering (QA) system that answers questions based on the content of a PDF file. It uses LangChain for document processing and GPT-4 for generating answers. The process includes loading a PDF, indexing its content, and answering user queries.

## Key Features:
- Loads and extracts content from a PDF.
- Indexes the content using a vector store for efficient retrieval.
- Uses GPT-4 for generating answers based on the extracted content.

## Requirements:
- Python 3.7+
- `pydantic`, `langchain_core`, `langchain_openai`, `langgraph`, `openai`

## Setup:
1. Clone the repository:
   ```bash
   git clone https://github.com/djinn09/langchain_pdf_qa
   cd your-repository-name
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Set up OpenAI API key.

## Code Overview:

1. **PDF Loading**: `pdf_loader(file_path)` extracts pages from a PDF using `PyPDFLoader`.
2. **Vector Store**: `create_vector_store(pages)` creates an in-memory vector store from the extracted PDF pages using `OpenAIEmbeddings`.
3. **User Input**: `UserInput` defines the input structure, including the PDF file path and questions.
4. **QA Function**: `retrival_qa(questions, vector_store)` retrieves relevant content from the vector store and generates answers with GPT-4.
5. **Custom Tool**: `RetrivalQA` is a LangChain tool that integrates the retrieval and QA process.
6. **Agent Creation**: An agent is created using `create_react_agent` to interact with the language model and answer questions.

## Running the Code:
To run the system and get answers, invoke the agent with a message like this:

```python
agent_executor.invoke({
    "messages": [
        HumanMessage(content="""File_Path:/content/handbook.pdf
        Questions:
        What is the name of the company?
        Who is the CEO of the company?""")
    ]
})
```
---
