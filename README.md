Notebook LLM Clone

Notebook LLM Clone is a NotebookLM-style AI learning assistant that lets users upload and process multiple source types such as PDF, text, Markdown, and YouTube content, chat with their sources using RAG, generate learning tools, and manage user memories.

About the Project

The project combines document processing, vector search, LLM generation, and memory to create an AI-powered study workspace.

Core Features

Authentication and protected workspaces

Multi-source upload and processing (PDF, text, Markdown, YouTube, etc.)

Document chunking and embeddings

Semantic search with Pinecone

RAG-based chat over uploaded sources

AI-generated learning tools:

Summary

Takeaways

Flashcards

Quiz

Mindmap

Report

User memory with Mem0

Background processing with Inngest

PDF storage with Cloudinary

Project Logic

User
  |
  v
Next.js Client
  |
  v
Express API
  |
  +--> Authentication / Workspace
  |
  +--> Source Upload
  |       |
  |       v
  |    Cloudinary
  |       |
  |       v
  |    Inngest
  |       |
  |       v
  |    PDF Text Extraction
  |       |
  |       v
  |    Chunking
  |       |
  |       v
  |    OpenAI Embeddings
  |       |
  |       v
  |    Pinecone
  |
  +--> Chat
  |       |
  |       v
  |    Query Embedding -> Pinecone Retrieval
  |       |
  |       v
  |    Relevant Context -> OpenAI -> Answer
  |
  +--> Memory
          |
          v
        Mem0

A source becomes READY after its content is extracted, chunked, embedded, and successfully indexed in Pinecone. Only ready sources are used for learning-tool generation.

Architecture

+-----------------------+
|     Next.js Client    |
|        :3000          |
+-----------+-----------+
            |
            | HTTP
            v
+-----------------------+
| Express / TypeScript  |
|        :8080          |
+-----+-------+------+--+
      |       |      |
      v       v      v
 PostgreSQL  Mem0  OpenAI
      |              |
      |              v
      |          Embeddings
      |              |
      |              v
      |           Pinecone
      |
      +-- Prisma / Better Auth

Background processing:
Express -> Inngest -> PDF processing -> Embeddings -> Pinecone

File storage:
Client -> Express -> Cloudinary

Tech Stack

Frontend

Next.js

React

TypeScript

Tailwind CSS

shadcn/ui

Backend

Node.js

Express

TypeScript

Prisma

PostgreSQL

Better Auth

AI / RAG

OpenAI

text-embedding-3-small

Pinecone

Mem0

Infrastructure / Services

Docker

Inngest

Cloudinary

Project Structure

notebook-llm-clone/
├── client/              # Next.js frontend
├── server/              # Express backend
│   ├── src/
│   │   ├── controllers/
│   │   ├── services/
│   │   ├── repositories/
│   │   ├── lib/
│   │   └── ...
│   └── prisma/
├── docker-compose.yml
└── README.md

Environment Variables

Configure the required variables in server/.env.

DATABASE_URL=
OPENAI_API_KEY=

PINECONE_API_KEY=
PINECONE_INDEX=

MEM0_API_KEY=

CLOUDINARY_CLOUD_NAME=
CLOUDINARY_API_KEY=
CLOUDINARY_API_SECRET=
CLOUDINARY_UPLOAD_PRESET=

Never commit .env or API secrets to GitHub.

Run the Project

1. Start Docker

From the project root:

docker compose up -d

2. Start Backend

cd server
npm run dev

Backend:

http://localhost:8080

3. Start Inngest

Open another terminal:

cd server
npx inngest-cli@latest dev

Inngest dashboard:

http://localhost:8288

4. Start Frontend

Open another terminal:

cd client
npm run dev

Frontend:

http://localhost:3000

Startup Order

Docker -> Server -> Inngest -> Client

Prisma Client generation is already included in the server development command, so Prisma normally does not need to be run separately every time.

Functional Test

After starting the project:

Open http://localhost:3000

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
