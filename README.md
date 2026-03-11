# Keonhee Kim — Agentic AI Developer

**Business Administration, Sungkyunkwan University (SKKU), South Korea.**

I build production agentic AI systems that automate business workflows — not demos, not tutorials. Deployed, working software.

Unique profile: **AI technical depth + business/consulting background.** I design multi-agent systems and understand the business problems they solve. That combination is rare at student level.

---

## Projects

### FinAgent — Multi-Agent Financial Analysis System
**Live:** [keonhee-finagent.streamlit.app](https://keonhee-finagent.streamlit.app) &nbsp;|&nbsp; [GitHub](https://github.com/keonhee3337-art/FinAgent)

Automates financial analysis workflows for Korean public companies using a three-agent LangGraph pipeline. What previously required an analyst to write SQL, search documents, and synthesize a report now happens in a single natural language query.

**Architecture:**
- **Orchestration:** LangGraph `StateGraph` with typed `AgentState`. Streaming output via `graph.stream(stream_mode="values")`.
- **SQL Agent:** GPT-4o generates SQL with schema injection → executes against SQLite (Samsung Electronics, SK Hynix, LG Electronics, 2020–2024)
- **RAG Agent:** Custom vector database (OpenAI `text-embedding-3-small`, 1536 dims, NumPy cosine similarity). Built from scratch — no ChromaDB, no Pinecone.
- **Report Agent:** GPT-4o synthesizes SQL results + RAG findings → structured markdown report
- **Backend:** FastAPI (async, `POST /analyze`)
- **Frontend:** Streamlit (streaming, per-session thread IDs, cached graph)

**Key decision documented:** ChromaDB incompatible with Python 3.14 (Pydantic v1 issue). Built custom VectorDB instead. Zero external dependencies for retrieval.

---

### DART MCP Server — Korean Financial Data as an AI Tool
**GitHub:** [dart-mcp-server](https://github.com/keonhee3337-art/dart-mcp-server)

A custom MCP (Model Context Protocol) server that exposes real-time Korean corporate financial data from DART (Korea Financial Supervisory Service) as tools for Claude Code and AI agents.

**What it enables:** Any MCP-compatible AI agent can query Samsung's latest earnings, check SK Hynix disclosures, or pull LG Electronics balance sheets — directly in conversation, no browser or manual API calls.

**Tools:** `search_company` · `get_financials` · `get_company_info` · `get_disclosures`

**Coverage:** All ~2,500+ Korean public companies on KOSPI and KOSDAQ.

**Architecture:** Python MCP SDK (stdio transport) + dart-fss library → DART FSS Open API. ~300 lines of Python. Connected and active in Claude Code.

**Why this is a moat:** DART integration is non-trivial for international AI tools. Korean-language company search, corporate structure, and financial statement formats require domain knowledge most tools don't have.

---

### DART Financial App — Samsung Data Analysis
**Live:** [keonhee-strategy.streamlit.app](https://keonhee-strategy.streamlit.app)

Samsung Electronics financial data via DART API → SQLite → RAG pipeline → GPT-4o analysis → Streamlit frontend. Deployed on Streamlit Cloud.

---

### RAG Demo — Production Retrieval Pipeline

FastAPI + Pinecone + Supabase + GPT-4o. OpenAI `text-embedding-3-small` embeddings. Multi-turn conversation history in Supabase. Live via ngrok for demos.

---

### SDC Consulting Club — AI-Powered Application Review

Built an automated application review system for SKKU's SDC Consulting Club. Gmail → PDF extraction → Claude Haiku API grading (structured rubric) → Google Sheets logging. Runs every 15 minutes via Google Apps Script. Eliminated manual review for initial screening.

---

## Technical Stack

| Category | Tools |
|----------|-------|
| Agent orchestration | LangGraph (StateGraph, conditional edges, streaming, checkpointing) |
| Retrieval | RAG, custom VectorDB (cosine similarity), Pinecone, Text2SQL |
| LLM APIs | OpenAI GPT-4o, OpenAI Embeddings, Claude API (Haiku, Sonnet) |
| Tooling | MCP (Model Context Protocol), Claude Code |
| Backend | FastAPI (async, CORS), SQLite, Supabase (Postgres) |
| Frontend | Streamlit (streaming, session state, caching) |
| Data | DART FSS API (Korean corporate filings), yfinance |
| Languages | Python — numpy, pandas, asyncio |

---

## Background

Business Administration at SKKU. Active in SDC Consulting Club. Building expertise in agentic AI systems — specifically where AI engineering meets business applications.

Focus areas: multi-agent coordination, Korean market data, financial analysis automation, MCP tooling.

I design systems end-to-end: problem definition → architecture → implementation → deployment → documented tradeoffs.

---

## Live Projects

- **FinAgent:** [keonhee-finagent.streamlit.app](https://keonhee-finagent.streamlit.app)
- **DART App:** [keonhee-strategy.streamlit.app](https://keonhee-strategy.streamlit.app)
