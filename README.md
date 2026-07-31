# Commit Roast Bot 🔥

An n8n automation that fetches my latest GitHub commit every few hours and roasts it using a locally-running AI model — then sends the roast straight to Telegram.

## What it does

1. **Schedule Trigger** — runs automatically every 6 hours
2. **GitHub API** — fetches the latest commit from a target repo
3. **Ollama (llama3.2)** — a local AI model generates a short, witty roast of the commit message
4. **Telegram** — sends the roast as a message

100% free and local — no OpenAI API key needed. Uses [Ollama](https://ollama.com) running on my machine for both the chat model and embeddings.

## Stack

- [n8n](https://n8n.io) — workflow automation
- [Ollama](https://ollama.com) — local LLM runtime (`llama3.2` for chat, `nomic-embed-text` for embeddings)
- GitHub API — commit data source
- Telegram Bot API — message delivery

## Workflows

- `Commit_Roast_-_Ingestion.json` — embeds past commit messages into a local vector store (for future contextual roasts)
- `Commit_Roast_-_Live.json` — the live pipeline: fetch latest commit → generate roast → send to Telegram

## Setup

1. Install [Ollama](https://ollama.com) and pull models:

2. Import the workflow JSON files into your own n8n instance
3. Add your own GitHub Personal Access Token and Telegram Bot credentials
4. Activate the "Live" workflow
