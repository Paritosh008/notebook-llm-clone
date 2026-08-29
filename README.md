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


Learning Tool	Purpose
📄 Summary	Understand the complete material quickly
💡 Takeaways	Extract important concepts
🎴 Flashcards	Create revision material
❓ Quiz	Test understanding
🗺️ Mindmap	Visualize relationships between concepts
📑 Report	Generate structured long-form content
🏗️ Architecture
Next.js Client
      ↓
Express API
      ↓
PostgreSQL + Prisma
      │
      ├── OpenAI
      ├── Pinecone
      ├── Mem0
      ├── Inngest
      └── Cloudinary

      🛠️ Tech Stack

Frontend: Next.js, React, TypeScript, Tailwind CSS, shadcn/ui

Backend: Node.js, Express, TypeScript, Prisma, PostgreSQL, Better Auth

AI / RAG: OpenAI, AI SDK, Embeddings, Pinecone, RAG

Memory: Mem0

Infrastructure: Docker, Inngest, Cloudinary
📁 Project Structure
notebook-llm-clone/
├── client/              # Next.js frontend
├── server/              # Express backend
├── docker-compose.yml
└── README.md

▶️ Run Locally
1. Start Docker
   docker compose up -d
2. Start Backend
   cd server
npm run dev
3. Start Inngest
   cd server
npx inngest-cli@latest dev
4. Start Frontend
   cd client
npm run dev

🧪 Functional Test
Login / create an account
Create a workspace
Upload a source
Wait until the source becomes READY
Ask questions in Chat
Generate learning tools from Learn
Test Memory
🎯 Key Concepts
Retrieval-Augmented Generation (RAG)
Vector Database & Semantic Search
Text Embeddings
Large Language Models (LLMs)
AI Memory
Background Job Processing
Document Processing
Structured LLM Output
📌 Project Status

✅ Working — Portfolio Project
    Built to demonstrate practical AI/GenAI engineering concepts and end-to-end LLM application development.  
