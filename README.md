# bet-ai-automation
Infraestrutura de suporte conversacional com inteligência artificial, construída com N8N, OpenAI, Redis, PostgreSQL e Supabase.


# Intelligent Betting Support System

Sistema de automação conversacional inteligente desenvolvido com N8N, OpenAI, Redis, PostgreSQL, Supabase e Crisp para atendimento automatizado em plataformas de apostas.

O projeto realiza atendimento automatizado em tempo real, classificação de intenção, memória contextual, handoff para suporte humano e gerenciamento inteligente de conversas.

---

# Features

- Atendimento automatizado com IA
- Classificação automática de intenção
- Encaminhamento inteligente para suporte humano
- Tagueamento automático de conversas no Crisp
- Distribuição automática de atendentes
- Memória contextual com Redis e PostgreSQL
- RAG com Supabase Vector Store
- Suporte a mensagens multimodais
- Controle anti-flood e anti-loop
- Structured Outputs via OpenAI
- Processamento assíncrono de mensagens
- Respostas otimizadas para WhatsApp

---

# Stack

## Orquestração
- N8N

## Inteligência Artificial
- OpenAI GPT-4o
- LangChain Nodes

## Banco de Dados
- PostgreSQL
- Redis
- Supabase

## Atendimento
- Crisp Chat API

---

# Arquitetura

```txt
User
  ↓
Crisp Chat
  ↓
N8N Webhook
  ↓
Message Processing Layer
  ↓
Redis Buffer + Session Control
  ↓
Intent Analysis
  ↓
AI Agent (GPT-4o)
  ↓
RAG (Supabase Vector Store)
  ↓
Response Processing
  ↓
Crisp Conversation Delivery
```

---

# Fluxo do Sistema

## 1. Recebimento da Mensagem
As mensagens chegam via webhook do Crisp.

## 2. Processamento Inicial
O sistema:
- identifica usuário
- valida sessão
- evita loops
- realiza controle anti-spam

## 3. Agrupamento de Mensagens
Mensagens consecutivas são agrupadas utilizando Redis para melhorar contexto e reduzir custo de inferência.

## 4. Classificação de Intenção
A IA identifica automaticamente intenções como:
- depósito
- saque
- suporte humano
- cadastro
- acesso
- palpites
- grupo VIP
- aprender a jogar

## 5. Memória Conversacional
O histórico é armazenado em PostgreSQL utilizando memória contextual.

## 6. RAG
O sistema consulta a base vetorial no Supabase para responder perguntas sobre:
- regras
- depósito
- saque
- bônus
- funcionamento da plataforma

## 7. Handoff Humano
Quando necessário:
- a conversa é tagueada no Crisp
- um atendente é atribuído automaticamente
- o usuário é encaminhado para suporte humano

---

# Principais Recursos Técnicos

## Structured Outputs
O agente utiliza respostas estruturadas em JSON para maior previsibilidade do fluxo.

## Redis Queue Buffer
Mensagens rápidas são agrupadas antes da inferência da IA.

## Anti Fragmentação
Sistema inteligente para evitar envio isolado de emojis e mensagens quebradas.

## Multi-Agent Workflow
O projeto utiliza sub-workflows especializados:
- transcrição
- análise de intenção
- registro de usuário
- processamento principal

---

# Segurança

- Variáveis sensíveis protegidas por ENV
- Controle de sessão
- Bloqueio temporário anti-loop
- Restrições de escopo no prompt
- Proteção contra prompt injection

---

# Estrutura do Projeto

```txt
project/
│
├── workflows/
├── prompts/
├── docs/
├── assets/
├── docker/
├── database/
└── README.md
```

---

# Possíveis Melhorias Futuras

- Dashboard analítico
- Fine-tuning de intenções
- Métricas de atendimento
- Observabilidade
- Voice AI
- Multi-tenant support
- Rate limiting avançado

---
