---
title: "optix-ai"
date: 2025-01-01
description: "Open-source FinOps agent that makes your cloud spend smarter — multi-account AWS cost optimization with LLM-powered recommendations."
github: "https://github.com/techtious/optix-ai"
tags: ["python", "aws", "llm", "agent", "finops", "claude", "fastapi", "multi-account"]
status: "active"
---

optix-ai is an open-source FinOps agent that connects to AWS Cost Explorer and uses an LLM to generate prioritized, actionable cost optimization reports. It supports multi-account setups, tag-based resource governance, and exports polished HTML reports for client sharing. Point it at your AWS account and it tells you exactly where money is being wasted and what to do about it.

## What it does

- **Cost breakdown** — top services by spend over the last 30 days
- **Trend analysis** — month-over-month changes for the last 3 months
- **EC2 rightsizing** — identify oversized instances and estimated savings
- **Savings Plans** — committed-use discount recommendations
- **Anomaly detection** — unexpected cost spikes above a configurable threshold
- **Multi-provider** — supports Anthropic Claude (default), Google Gemini, and DeepSeek
- **Multi-account** — manage and analyze multiple AWS accounts from a single CLI
- **Tag governance** — discover and audit resource tags for compliance and cost allocation
- **Report export** — save reports as Markdown or polished HTML for client sharing
- **Authentication** — built-in auth system for secure multi-user access

## Why I built it

Cloud costs are opaque. AWS bills are long, tooling is expensive, and most FinOps platforms are built for enterprises with dedicated teams. I wanted something lightweight that an engineer could run from the terminal and immediately get actionable output — no dashboards, no SaaS subscription, just a report. As the project grew, I added multi-account support and HTML reports to make it useful for consultants and teams managing multiple clients.

## Usage

```bash
# Generate and display a report (uses Claude by default)
optix

# Use Gemini instead
optix --provider gemini

# Save report to a Markdown file
optix --save

# Save to a specific directory without printing to terminal
optix --save ./reports --no-display

# Discover and audit resource tags
optix --tag-discover
optix --tag-audit
```

Each report includes an executive summary, service breakdown, ranked optimization recommendations, anomaly flags, and a numbered action plan.

## Stack

Python 3.11+, AWS Cost Explorer API, Anthropic Claude / Google Gemini / DeepSeek, FastAPI, SQLAlchemy, Alembic
