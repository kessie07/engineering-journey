# RepoMind

**Status:** Built / worked on (team project, not production-ready yet)
**When:** July – August 2026
**Code:** Private for now

## What it is

You point RepoMind at a GitHub repository and then ask questions about the code. It pulls the repo's files through the GitHub API, splits them into chunks, embeds them, stores them in Qdrant, and answers your question with Gemini using the most relevant chunks as context.

This was a team project. This page covers the project as a whole. I'll add a clearer breakdown of the parts I worked on as I go back through it.

## How it's put together

```text
Next.js frontend
      │  REST
      ▼
FastAPI backend
  ├── GitHub service   → fetch repo tree + files, filter, chunk
  ├── Gemini service   → embeddings (gemini-embedding-001), answers (gemini-2.5-flash)
  └── Vector DB layer  → Qdrant
```

- **Backend** (Python, FastAPI, Pydantic, PyGithub, qdrant-client, google-genai). Endpoints for health, ingestion (runs as a background task you poll for status), querying, listing repos and indexed files, and inspecting or clearing the vector collection.
- **Frontend** (Next.js 16, React 19, TypeScript, Tailwind). Landing page, login, and a workspace with a repository overview, dependency graph, AI assistant chat, documentation explorer, ingest dialog and settings.
- **Ops**: Dockerfiles, docker-compose, and a deploy script for AWS EC2. There's one backend API test file (unittest).

## Where it actually is

From my own project notes (Aug 2026):

- **Working**: GitHub ingestion, backend, repository processing, vector search, AI answers
- **Broken**: the frontend wasn't loading correctly, so the full flow wasn't verified end to end
- **Goal at the time**: make it stable and demo-ready

A big chunk of the commit history is a fight with a small EC2 instance: Next.js builds running out of memory, Docker layers filling the disk, adding swap and then removing it again, and finally running the frontend directly on the host with only the backend in Docker. That's the most "real-world" thing about this project so far, and I want to write it up properly.

## What's next

- Get the frontend working again and verify ingest → query → answer end to end
- Finish the architecture and decision notes I started. For example, I listed Qdrant vs pgvector vs Chroma but never wrote down *why* Qdrant.
- More tests than a single API test file

## Evidence

- **Architecture**: the diagram above is based on the actual code layout (`app/services/github.py`, `app/services/gemini.py`, `app/database/vector_db.py`, `components/workspace/*`).
- **Notes**: I kept an Obsidian vault for this (dashboard, data flow, RAG architecture, ADR-001 on the vector DB, bug log). Cleaned-up versions will move here.
- **Screenshots**: none yet. I'll add them once the frontend is fixed, not before.
