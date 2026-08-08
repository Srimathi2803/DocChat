# DocChat 💬📄

A conversational RAG (Retrieval-Augmented Generation) app that lets you upload PDF documents and chat with them in natural language — with full conversation memory and LLM observability.

## 🔍 What it does

Upload one or more PDFs, and ask questions about their content in plain English. DocChat retrieves the most relevant chunks from your documents using a vector store, feeds them to an LLM along with your chat history, and returns grounded, context-aware answers — so it remembers what you asked earlier in the conversation, not just the current question.

## ✨ Features

- 📤 **PDF upload** — chat with any PDF document directly
- 🧠 **Conversational memory** — maintains chat history across turns for natural follow-up questions
- 🔎 **Retrieval-Augmented Generation (RAG)** — answers are grounded in your document content, not just the LLM's general knowledge
- 🗄️ **Vector search with ChromaDB** — fast, scalable similarity search over document embeddings
- ⚡ **Groq API + Gemma LLM** — low-latency inference for fast responses
- 📊 **LangSmith tracing** — every chain run is traced and observable for debugging and evaluation
- 🎛️ **Streamlit UI** — simple, interactive web interface

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| LLM | Gemma (via Groq API) |
| Framework | LangChain |
| Vector Database | ChromaDB |
| Observability | LangSmith |
| Frontend | Streamlit |
| Language | Python |

## 🏗️ How it works

1. User uploads a PDF through the Streamlit interface
2. The document is split into chunks and converted into embeddings
3. Embeddings are stored in ChromaDB (vector store)
4. On each user question, relevant chunks are retrieved via similarity search
5. Retrieved context + chat history + the question are passed to the Gemma LLM (via Groq)
6. The LLM's response is streamed back to the user, and the exchange is added to conversation memory
7. LangSmith traces the full chain execution for debugging and monitoring

## 📸 Screenshots
![Upload and chat interface](<img width="1536" height="864" alt="DocChatSS4" src="https://github.com/user-attachments/assets/e724d021-f834-4de9-8f83-b77557d73a32" />
)
![Conversation with follow-up questions](<img width="1543" height="878" alt="DocChatSS3" src="https://github.com/user-attachments/assets/6f0f9251-fb55-4ca0-ab37-a7caaf643a3d" />
)
<img width="965" height="852" alt="DocChatSS2" src="https://github.com/user-attachments/assets/4100c271-308c-4275-a665-a6f6d426eacc" />
<img width="1145" height="739" alt="DocChatSS1" src="https://github.com/user-attachments/assets/c5723d2e-167c-4a38-8b53-54c8adaa5913" />
<img width="1713" height="862" alt="DocChatSS5" src="https://github.com/user-attachments/assets/1a24e583-822b-4e54-aa53-57d5c5d2522c" />

## 🚀 Live Demo

🔗 [Try DocChat live](https://docchat-khh22ckwxsssct5hwz39ac.streamlit.app/)

## ⚙️ Setup & Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Srimathi2803/DocChat.git
   cd DocChat
   ```

2. **Create a virtual environment and install dependencies**
   ```bash
   python -m venv venv
   source venv/bin/activate   # On Windows: venv\Scripts\activate
   pip install -r requirements.txt
   ```

3. **Set up your API keys**

   Create a `.streamlit/secrets.toml` file (this file is git-ignored and should never be committed) with:
   ```toml
   GROQ_API_KEY = "your-groq-api-key"
   ASTRA_DB_API_ENDPOINT = "your-astradb-endpoint"
   ASTRA_DB_APPLICATION_TOKEN = "your-astradb-token"
   LANGCHAIN_API_KEY = "your-langsmith-api-key"
   LANGCHAIN_TRACING_V2 = "true"
   ```

4. **Run the app**
   ```bash
   streamlit run ragApp/app.py
   ```

## 📌 Future Improvements

- Support for multiple file formats (DOCX, TXT, web pages)
- Multi-document querying in a single session
- User authentication and persistent chat sessions
- Source citation for retrieved answers

## 👩‍💻 Author

**Srimathi K**
[GitHub](https://github.com/Srimathi2803) 

---
*Built as part of a self-directed learning project in Generative AI, LangChain, and RAG systems.*
