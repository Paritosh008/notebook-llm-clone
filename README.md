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
  
  
Environment Variables
Configure the required variables in `server/.env`.
```env
DATABASE\_URL=
OPENAI\_API\_KEY=

PINECONE\_API\_KEY=
PINECONE\_INDEX=

MEM0\_API\_KEY=

CLOUDINARY\_CLOUD\_NAME=
CLOUDINARY\_API\_KEY=
CLOUDINARY\_API\_SECRET=
CLOUDINARY\_UPLOAD\_PRESET=
```
Never commit `.env` or API secrets to GitHub.
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
Prisma Client generation is already included in the server development command, so Prisma normally does not need to be run separately every time.
Functional Test
After starting the project:
Open `http://localhost:3000`
Login / create an account
Create a workspace
Upload a PDF from Sources
Wait for processing to complete
Verify the source becomes READY
Open Chat and ask questions about the uploaded document
Open Learn and generate Summary, Takeaways, Flashcards, Quiz, Mindmap, or Report
Open Memory and test adding/updating/deleting memories
Verify RAG answers use information from the uploaded source
RAG Flow
```text
PDF
 |
 v
Text Extraction
 |
 v
Chunking
 |
 v
OpenAI Embeddings
 |
 v
Pinecone Vector Index
 |
 v
User Question
 |
 v
Question Embedding
 |
 v
Similarity Search
 |
 v
Relevant Chunks
 |
 v
LLM Context
 |
 v
Answer
```
Key Concepts
RAG: Grounds chat responses in uploaded source content.
Vector Database: Pinecone stores and retrieves document embeddings.
Embeddings: OpenAI converts text into vectors for semantic search.
Inngest: Handles background source-processing jobs.
Mem0: Stores and retrieves user memories.
Cloudinary: Stores uploaded PDF files.
PostgreSQL + Prisma: Stores application data such as users, workspaces, sources, conversations, and artifacts.
License
This project is intended for learning, portfolio, and demonstration purposes.
