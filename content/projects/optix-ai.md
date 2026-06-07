---
title: "optix-ai"
date: 2025-01-01
description: "Open-source LLM FinOps agent that turns an AWS bill into a ranked action plan."
github: "https://github.com/techtious/optix-ai"
tags: ["python", "aws", "llm", "agent", "finops", "claude"]
status: "active"
---

optix-ai connects to AWS Cost Explorer and uses an LLM to generate prioritized, actionable cost optimization reports. Point it at your AWS account and it tells you exactly where money is being wasted and what to do about it.

## What it does

- **Cost breakdown** — top services by spend over the last 30 days
- **Trend analysis** — month-over-month changes for the last 3 months
- **EC2 rightsizing** — identify oversized instances and estimated savings
- **Savings Plans** — committed-use discount recommendations
- **Anomaly detection** — unexpected cost spikes above a configurable threshold
- **Multi-provider** — supports Anthropic Claude (default) and Google Gemini
- **Report export** — save the full report as a Markdown file

## Why I built it

Cloud costs are opaque. AWS bills are long, tooling is expensive, and most FinOps platforms are built for enterprises with dedicated teams. I wanted something lightweight that an engineer could run from the terminal and immediately get actionable output — no dashboards, no SaaS subscription, just a report.

## Usage

```bash
# Generate and display a report (uses Claude by default)
optix

# Use Gemini instead
optix --provider gemini

# Save report to a file
optix --save
```

Each report includes an executive summary, service breakdown, ranked optimization recommendations, anomaly flags, and a numbered action plan.

## Stack

Python 3.11+, AWS Cost Explorer API, Anthropic Claude / Google Gemini
