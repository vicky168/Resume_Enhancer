# Resume_Enhancer

# 🤖 RAG Resume Chatbot using n8n, Google Gemini & Pinecone

This project demonstrates how to build a **Retrieval-Augmented Generation (RAG) chatbot** that intelligently answers questions based on resume documents using **n8n**. The chatbot uses **Google Gemini (PaLM)** for embeddings and chat completion, **Pinecone** as the vector store, and integrates with **Google Drive** to fetch resumes.

## 📌 Features

- ✅ Automated monitoring of a Google Drive folder for new/updated resume files.
- ✅ Vectorization of document content using Google Gemini embeddings.
- ✅ Storage of vector data in Pinecone.
- ✅ RAG-enabled chatbot capable of answering resume-specific queries.
- ✅ Deployed within n8n workflow automation.

---

## 🧠 Use Case

🎯 **Resume Verifier Chatbot for Recruiters or Portfolio Projects**

Ask the chatbot:
> - "What is John Doe's experience in AI?"
> - "List certifications from this resume."
> - "Does this resume include internship details?"

Great for:
- Personal portfolio projects to showcase LLM pipeline skills.
- HR teams who want automated resume parsing + Q&A.
- Enhancing your resume with AI tool-building experience.

---

## 📁 Tech Stack

| Component | Role |
|----------|------|
| `n8n` | No-code workflow automation platform |
| `Google Gemini` | Embedding model and language model |
| `Google Drive` | Storage for resumes (PDFs, DOCs, etc.) |
| `Pinecone` | Vector store for fast document retrieval |
| `LangChain` | Orchestration between components |

---

## 🔧 Setup Instructions

### 1. Prerequisites

- ✅ A **Google Cloud** project with **Vertex AI API** enabled.
- ✅ Google **PaLM/Gemini API Key** from AI Studio.
- ✅ **Pinecone** account with an index (e.g. `rag-n8n`).
- ✅ Create a **Google Drive folder** for uploading resumes.
- ✅ Setup an **n8n instance** (Cloud or Self-hosted).

### 2. Add Credentials in n8n

Configure credentials in your n8n environment for:

- `Google Drive OAuth2`
- `Google Gemini (PaLM) API Key`
- `Pinecone API`

### 3. Import the Workflow

Import the `Rag_gemini.json` file into n8n. You can do this via:

> Settings → Import Workflow → Select JSON file

### 4. Configure Nodes

- Update the **Google Drive Trigger** nodes to monitor your folder.
- Set your **Pinecone index name** (e.g., `rag-n8n`) in vector store nodes.
- Confirm Google Gemini nodes use the correct model (`text-embedding-004`, `gemini-2.0-flash-exp`).

---

## 📊 Workflow

Here’s a visual representation of the RAG workflow inside n8n:

> _You can add images below to visually explain the workflow._

### 🔁 Full Workflow Screenshot

![image](https://github.com/user-attachments/assets/ece3391c-9f47-484e-9efc-1523f20ef606)


### 🧠 AI Embedding + Pinecone Vectorization

![image](https://github.com/user-attachments/assets/8e8516fa-98c1-4034-a236-9beb5c0c1a38)


### 💬 Chatbot Interaction Path

![image](https://github.com/user-attachments/assets/c68c4208-3053-41ba-8b08-9b1db6a645cd)


---

## 💬 How It Works

1. 📁 **Drive Upload**  
   You upload a new or updated resume to a designated Google Drive folder.

2. ⚙️ **n8n Workflow Triggered**  
   The workflow detects the change and downloads the file.

3. 📄 **Document Loader + Splitter**  
   The file is chunked using a character text splitter.

4. 🧠 **Embedding & Indexing**  
   Chunks are embedded with Google Gemini and stored in Pinecone.

5. 💬 **Chat Interface**  
   A chatbot (powered by LangChain) answers user queries using RAG from Pinecone.

---

## 🧪 Sample Prompt

```plaintext
Hi! I am your Resume Assistant. Ask me anything about the uploaded resumes.
