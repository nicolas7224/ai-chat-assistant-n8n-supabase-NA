# 🤖 AI Chat Assistant with n8n + Supabase RAG

This project is an **AI-powered personal assistant** built on [n8n](https://n8n.io).  
It uses **RAG (Retrieval-Augmented Generation)** with **Supabase** to answer questions based on personal documents stored in Google Drive.


## ☁️ Deployment Server

This project runs on **AWS EC2 (Ubuntu 24.04)**.

- Instance type: t3.small (2 vCPU, 2GB RAM)
- Environment: Docker + n8n
- APIs configured: WhatsApp, Google Drive, Supabase, OpenAI
- Persistent storage: PostgreSQL (Supabase) + Google Sheets for logging

✅ This makes the assistant cloud-ready and demonstrates end-to-end deployment (LLMOps).


## ☁️ Deployment with Docker + Easypanel

The assistant is deployed on **AWS EC2 (Ubuntu 24.04)** using **Docker containers** managed by [Easypanel](https://easypanel.io).

### Running services:
- **n8n** → Workflow orchestration
- **PostgreSQL** → Database for conversation storage
- **Redis** → Cache and job queue management
- **Evolution-API** → WhatsApp integration layer
- **Supabase** → Vector database (pgvector) for embeddings
- **OpenAI** → LLMs, embeddings, transcription, image analysis

### Benefits:
- Containerized and reproducible environment  
- Scalable with Docker Compose/Easypanel  
- Easy monitoring and redeployment  

---

## ✨ Features

- **Chat classification**:
  - If the chat is from me → Acts as a **personal assistant** (manages Google Calendar, tasks, etc.).
  - If the chat is from someone else → Responds in a natural way using **OpenAI LLM**.
- **RAG integration**:
  - Monitors a Google Drive folder for new documents (PDF, TXT, etc.).
  - Automatically generates **embeddings with OpenAI**.
  - Stores embeddings + content in **Supabase (PostgreSQL with pgvector)**.
  - Uses embeddings to provide context-aware answers.
- **Multi-modal AI**:
  - Audio transcription (speech-to-text with OpenAI Whisper).
  - Image analysis (OpenAI GPT-4o-mini).
- **Data persistence**:
  - Stores conversations in **PostgreSQL**.
  - Logs interactions into **Google Sheets** for reporting.
- **Integrations**:
  - **WhatsApp API** for real-time messaging.
  - **Google Calendar API** for scheduling.
  - **Google Drive API** for document ingestion.
  - **Supabase** for embeddings and semantic search.

---

## 🛠 Tech Stack

- [n8n](https://n8n.io) – Workflow orchestration  
- [Supabase](https://supabase.com) – Database + vector search (pgvector)  
- [OpenAI](https://platform.openai.com) – LLMs, embeddings, transcription, image analysis  
- [PostgreSQL](https://www.postgresql.org/) – Conversation history  
- [Google Drive API](https://developers.google.com/drive) – Document ingestion  
- [Google Calendar API](https://developers.google.com/calendar) – Assistant functions  
- [Google Sheets API](https://developers.google.com/sheets/api) – Logs and analytics  
- WhatsApp Business API – Real-time communication  

---

## 📂 Project Structure

- `AgentePrueba1_Supabase_Anonymized.json` → exported anonymized n8n workflow  
- `README.md` → documentation  

---

## 🚀 How It Works

1. **Document ingestion**  
   - Upload a new file into a dedicated Google Drive folder.  
   - n8n detects the change and extracts text.  
   - OpenAI creates embeddings → stored in Supabase.  

2. **Chat interaction**  
   - A user sends a message via WhatsApp.  
   - The agent classifies if it’s me or someone else.  
   - If the question requires context → retrieves relevant passages from Supabase (RAG).  
   - OpenAI LLM combines question + context → generates a precise answer.  

3. **Response delivery**  
   - Answer is sent back via WhatsApp API.  
   - Logs stored in Google Sheets + PostgreSQL.  

---

## 📸 Demo Screenshots

- n8n workflow view (document ingestion + assistant logic).
  
    <img width="2240" height="1282" alt="image" src="https://github.com/user-attachments/assets/112b4d12-bf6b-475a-bbbd-6f43d194875d" />

    
- Example of a document being added to Drive and indexed in Supabase.
  
    <img width="2558" height="1374" alt="image" src="https://github.com/user-attachments/assets/6b34f0c6-8ac7-4538-b4d0-51fba0c13110" />


- WhatsApp chat showing a context-aware RAG answer.
   
    <img width="1114" height="817" alt="image" src="https://github.com/user-attachments/assets/21c457a1-9fda-42a6-a211-84801ab3244a" />


---

## 🌟 Future Improvements

- Add support for **multi-channel messaging** (Telegram, Slack, email).  
- Enhance **task management** integration (Trello, Notion, Asana).  
- Build a **dashboard (Power BI / Streamlit)** for analytics.  
- Deploy via **Docker/Kubernetes** for production-ready MLOps.  

---

## 👤 Author

**Nicolás Ávila**  
Industrial Engineer | Data Analyst | Aspiring Data/AI Engineer  

- 🔗 [LinkedIn](https://www.linkedin.com/in/nicol%C3%A1s-avila-31380514a/)  
- 📧 Contact: nicolas7224@hotmail.com  



