# Notebook LLM Clone

Notebook LLM Clone is a NotebookLM-style AI learning assistant that lets users upload and process multiple source types such as **PDF, text, Markdown, and YouTube content**, chat with their sources using RAG, generate learning tools, and manage user memories.

## 🎯 What This Project Does

Instead of simply reading a document, users can turn their learning material into an interactive AI-powered study workspace.

### Core Features

- 📄 Upload and process multiple source types
  - PDF
  - Text
  - Markdown
  - YouTube
  - Other supported sources
- 💬 Chat with uploaded sources using RAG
- 🔎 Semantic search using vector embeddings
- 🧠 Generate AI-powered learning tools
  - Summary
  - Takeaways
  - Flashcards
  - Quiz
  - Mindmap
  - Report
- 🧠 Store and retrieve user memories using Mem0
- ⚡ Background source processing using Inngest
- ☁️ PDF storage using Cloudinary
- 🔐 Authentication and protected workspaces

---

## ⭐ Key Technical Highlights

### 🧠 Retrieval-Augmented Generation (RAG)

The application does not simply send the user's question directly to the LLM.

It first retrieves relevant information from the user's uploaded sources.

```text
User Question
      ↓
Generate Query Embedding
      ↓
Pinecone Semantic Search
      ↓
Retrieve Relevant Chunks
      ↓
Build Context
      ↓
LLM
      ↓
Context-Aware Answer



```
Run the Project
1. Start Docker
From the project root:
```powershell
docker compose up -d
```
2. Start Backend
```powershell
cd server
npm run dev
```
Backend:
```text
http://localhost:8080
```
3. Start Inngest
Open another terminal:
```powershell
cd server
npx inngest-cli@latest dev
```
Inngest dashboard:
```text
http://localhost:8288
```
4. Start Frontend
Open another terminal:
```powershell
cd client
npm run dev
```
Frontend:
```text
http://localhost:3000
```
Startup Order
```text
Docker -> Server -> Inngest -> Client
```
