---
title: "sovereign-ai-platform"
date: 2026-06-06
description: "Self-hostable RAG + agent serving platform for regulated, data-sovereign environments."
github: "https://github.com/connectwithrl/sovereign-ai-platform"
tags: ["python", "rag", "pgvector", "vllm", "mcp", "fastapi", "kubernetes", "observability"]
status: "active"
---

sovereign-ai-platform is the platform layer that turns an LLM into a dependable product: an inference gateway, a retrieval pipeline on PostgreSQL + pgvector, an agent/MCP tool surface, a grounding guardrail, and first-class observability — all behind small interfaces so the same image runs offline in CI or in production by changing environment variables only.

I built it to demonstrate the engineering that real applied AI demands inside regulated, data-sovereign settings (bilingual EN/AR public-sector context): serving within latency and cost budgets, keeping retrieval correct, proving answers are grounded, and keeping confidential data inside the boundary.

## What it does

- **Pluggable serving** — one interface over an OpenAI-compatible **vLLM/TGI** server, **AWS Bedrock**, or a deterministic offline backend for CI
- **RAG pipeline** — token-aware chunking, embeddings, **pgvector** with an HNSW cosine index, and two-stage retrieval (vector recall + reranking)
- **Grounding guardrail** — every answer is scored against its retrieved sources; low-confidence answers can be refused
- **Agent + MCP** — the same retrieval/answer primitives exposed as Model Context Protocol tools, so Claude Code or a Pydantic AI agent can drive the knowledge base
- **Observability** — LLM-specific Prometheus metrics (token throughput, output-length distribution, grounding score), a Grafana dashboard, and optional OpenTelemetry tracing
- **Deploy + CI** — Docker Compose, a Helm chart, and a GitHub Actions pipeline that runs the test suite plus a retrieval-quality eval gate

## Why I built it

The hard part of applied AI isn't the demo — it's everything around the model. I wanted a single, honest, runnable reference that shows the platform layer end to end: pluggable backends so it runs anywhere with no GPU and no API keys, decisions written down as ADRs, and grounding treated as an engineering guardrail rather than a research afterthought. It mirrors the kind of sovereign-inference platform a government or enterprise team actually has to operate.

## Design decisions (written down)

- **Pluggable backends behind interfaces** — same artifact runs hermetically in CI and swaps to vLLM/Bedrock + pgvector in production via config; no environment drift
- **pgvector over a dedicated vector DB** — fewer systems to certify inside a sovereign boundary, transactional consistency with the source documents, with the option to swap in a dedicated ANN service if scale demands
- **Grounding as a guardrail + CI eval** — answers are scored and gated; retrieval quality fails the build if it regresses

Built AI-native, with Claude Code as part of the workflow.

## Stack

Python 3.11+, FastAPI, PostgreSQL + pgvector, vLLM / AWS Bedrock, MCP, Prometheus + Grafana, OpenTelemetry, Docker, Helm, GitHub Actions
