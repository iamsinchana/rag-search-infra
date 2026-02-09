# RAG Search Infrastructure

A production-oriented **AI-powered semantic search backend** implementing
**Retrieval-Augmented Generation (RAG)** using a service-based architecture.

This project is intentionally backend- and infra-focused, designed to mirror
how internal knowledge search systems are built in real-world engineering teams.

---

## 🎯 Goals

- Build a **non-trivial backend system**, not a demo app
- Separate **API, ML, and retrieval concerns**
- Explore **RAG trade-offs**: latency, cost, relevance, hallucination control
- Practice **containerized, CI-enabled development**

---

## 🧠 System Overview
Client
↓
Go API Gateway
↓
Semantic Retrieval (Vector DB)
↓
Context Assembly
↓
LLM Answer Generation

Services communicate over HTTP and are deployed via Docker Compose.

---

## 🧱 Architecture

### 1. API Gateway (Go)
- Handles query requests
- Orchestrates retrieval + LLM calls
- Implements timeouts, retries, and caching
- Exposes a clean REST interface

### 2. Embedding Worker (Python)
- Ingests documents (Markdown, PDF, text)
- Chunks content using configurable strategies
- Generates vector embeddings
- Writes embeddings to vector storage

### 3. Vector Database
- Stores dense embeddings
- Performs semantic similarity search
- Tuned for low-latency top-k retrieval

---

## 🛠️ Tech Stack

### Backend
- Go (net/http)
- Python (ML pipelines)

### AI / ML
- Sentence Transformers / OpenAI Embeddings
- LLM: GPT-4 / Claude / Local LLM (configurable)
- Retrieval-Augmented Generation (RAG)

### Infra
- Docker & Docker Compose
- GitHub Actions (CI)
- Makefile-based workflows

---

## 📂 Repository Structure

services/
api-gateway/ # Go backend service
embedding-worker/ # Python ML service
infra/
docker-compose.yml # Local orchestration
.github/workflows/
ci.yml # CI pipeline
