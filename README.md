# Keonhee Kim — Agentic AI Developer

**Business Administration, Sungkyunkwan University (SKKU), South Korea.**

I build production agentic AI systems that automate business workflows — not demos, not tutorials. Deployed, working software.

Unique profile: **AI technical depth + business/consulting background.** I design multi-agent systems and understand the business problems they solve. That combination is rare at student level.

---

## Projects

### SME Business Diagnostic AI
**GitHub:** [sme-diagnostic-ai](https://github.com/keonhee3337-art/sme-diagnostic-ai)

Business owners describe their company and problem in plain language. A four-agent LangGraph pipeline structures the problem into a MECE driver tree, researches industry benchmarks via Perplexity, self-improves recommendations through an autoresearch loop, and auto-generates a 12-slide consulting deck — the same output structure used by BCG and McKinsey.

**Architecture:**
- **Problem Structurer:** `claude-sonnet-4-6` → MECE issue tree (3 levels, 6-10 branches) + 5 hypotheses
- **Benchmark Research:** Perplexity `sonar-pro` — one query per driver tree branch
- **Autoresearch Loop:** `claude-haiku-4-5-20251001` scores on relevance/specificity/actionability → `claude-sonnet-4-6` improves low-scoring items → repeats up to 8 iterations until avg >= 7.5
- **Deck Generator:** `python-pptx` → 12-slide consulting deck (executive summary, driver tree, gap analysis, recommendations, roadmap)
- **Frontend:** Streamlit with download button for the generated deck

**Demo case:** Korean automotive components manufacturer with 3-year operating margin decline. Driver tree decomposes into cost structure and revenue mix branches, cross-referenced against DART peer financials and Perplexity industry data.

---

### Korean SME Lead Intelligence + GEO Audit
**GitHub:** [lead-intelligence](https://github.com/keonhee3337-art/lead-intelligence)

Automates B2B lead generation for Korean SMEs. Screens Korean manufacturers from DART by ICP criteria, scores them on AI readiness, audits each company's AI discoverability (GEO score), and generates personalized Korean outreach emails with a Haiku self-improvement loop. Exports to Excel.

**Architecture:**
- **DART Screener:** `dart-fss` filters Korean public companies by revenue range, pulls 3Y financials
- **AI Readiness Scorer:** 4-dimension weighted score (financial health 30%, revenue CAGR 30%, company size 20%, DART disclosure recency 20%)
- **GEO Audit Agent:** Perplexity `sonar` + robots.txt check + HTML citability analysis → 0-100 score per company
- **Outreach Generator:** `claude-sonnet-4-6` drafts Korean email using DART financials + GEO score as context → `claude-haiku-4-5-20251001` scores and iterates up to 3 times
- **Export:** pandas → two-sheet Excel (rankings + outreach drafts)

---

### FinAgent — Multi-Agent Financial Analysis System
**Live:** [keonhee-finagent.streamlit.app](https://keonhee-finagent.streamlit.app) | [GitHub](https://github.com/keonhee3337-art/FinAgent)

Automates financial analysis workflows for Korean public companies using a three-agent LangGraph pipeline. What previously required an analyst to write SQL, search documents, and synthesize a report now happens in a single natural language query.

**Architecture:**
- **SQL Agent:** GPT-4o generates SQL with schema injection → executes against SQLite (Samsung, SK Hynix, LG, 2020-2024)
- **RAG Agent:** Custom vector database (OpenAI text-embedding-3-small, 1536 dims, NumPy cosine similarity) — built from scratch, no ChromaDB/Pinecone
- **Report Agent:** GPT-4o synthesizes SQL results + RAG findings → structured markdown report
- LangGraph StateGraph with streaming, FastAPI backend, Streamlit frontend

---

### M&A Due Diligence Suite
**Live:** [keonhee-duediligence.streamlit.app](https://keonhee-duediligence.streamlit.app) | [GitHub](https://github.com/keonhee3337-art/consulting-emulation)

AI-powered M&A analysis platform — valuation agent (DCF + comparable company analysis), hybrid search (BM25 + dense embeddings + RRF re-ranking), XGBoost financial distress model, auto-generated PPTX report. Deployed on Streamlit Cloud and AWS Lambda.

---

### DART MCP Server — Korean Financial Data as an AI Tool
**GitHub:** [dart-mcp-server](https://github.com/keonhee3337-art/dart-mcp-server)

Custom MCP (Model Context Protocol) server exposing real-time Korean corporate financial data from DART as tools for Claude Code and AI agents. Covers all ~2,500+ Korean public companies on KOSPI and KOSDAQ.

**Tools:** `search_company` · `get_financials` · `get_company_info` · `get_disclosures`

---

### Samsung Electronics Stock Forecast
**GitHub:** [AI-project/06_Samsung_Forecast](https://github.com/keonhee3337-art/AI-project/tree/main/06_Samsung_Forecast)

Dual-model time series analysis (Linear Regression + Prophet) on 10 years of Samsung Electronics (005930.KS) data. Live macro signals: USD/KRW exchange rate + Philadelphia Semiconductor Index (SOX).

---

## Technical Stack

| Category | Tools |
|----------|-------|
| Agent orchestration | LangGraph (StateGraph, conditional edges, streaming, autoresearch loops) |
| Retrieval | RAG, custom VectorDB (cosine similarity), Pinecone, Text2SQL, hybrid BM25+dense |
| LLM APIs | OpenAI GPT-4o, Claude Sonnet/Haiku (Anthropic SDK), Perplexity sonar-pro |
| Tooling | MCP (Model Context Protocol), Claude Code, python-pptx |
| Backend | FastAPI (async, CORS), SQLite, Supabase (Postgres), AWS Lambda |
| Frontend | Streamlit (streaming, session state, caching) |
| Data | DART FSS API (Korean corporate filings), dart-fss, yfinance |
| Languages | Python — numpy, pandas, asyncio |

---

## Background

Business Administration at SKKU. Chairman of SDC (SKKU-Deloitte Consulting) club. Building expertise in agentic AI systems — specifically where AI engineering meets business applications.

Focus areas: multi-agent coordination, Korean market data, financial analysis automation, consulting AI, MCP tooling.

---

## Live Projects

- **SME Diagnostic AI:** [github.com/keonhee3337-art/sme-diagnostic-ai](https://github.com/keonhee3337-art/sme-diagnostic-ai)
- **Lead Intelligence:** [github.com/keonhee3337-art/lead-intelligence](https://github.com/keonhee3337-art/lead-intelligence)
- **FinAgent:** [keonhee-finagent.streamlit.app](https://keonhee-finagent.streamlit.app)
- **M&A Due Diligence:** [keonhee-duediligence.streamlit.app](https://keonhee-duediligence.streamlit.app)
- **DART App:** [keonhee-strategy.streamlit.app](https://keonhee-strategy.streamlit.app)
