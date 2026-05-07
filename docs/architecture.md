# System Architecture

## Overview

The system is an AI-powered conversational automation infrastructure designed for betting platforms.

It combines:
- AI customer support
- conversational memory
- intent classification
- human handoff
- vector search (RAG)
- intelligent message orchestration

---

# Architecture Flow

```txt
User
  ↓
Crisp Chat
  ↓
N8N Webhook
  ↓
Message Processing Layer
  ↓
Redis Buffer
  ↓
AI Intent Analysis
  ↓
OpenAI Agent
  ↓
Supabase RAG
  ↓
Response Processing
  ↓
Crisp Delivery
```

---

# Core Components

## N8N
Workflow orchestration and automation engine.

## OpenAI
Responsible for:
- conversational responses
- intent analysis
- structured outputs

## Redis
Used for:
- buffering messages
- session control
- anti-flood protection
- temporary state management

## PostgreSQL
Stores:
- chat history
- contextual memory
- conversation logs

## Supabase
Used as vector database for retrieval augmented generation (RAG).

## Crisp
Customer support and live chat platform integration.

---

# Main Features

- AI support automation
- Human handoff system
- Intent classification
- Context-aware memory
- RAG integration
- Multi-workflow orchestration
- Structured outputs
- Anti-fragmentation logic