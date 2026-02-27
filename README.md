Altayeb, [2/27/2026 4:21 AM]
# 📱 Instagram Customer Service Automation

> An AI-powered customer service agent that handles Instagram DMs and comments — classifies intent, routes actions, logs data, and notifies your team in real time. Built with n8n + OpenRouter + MCP + Pinecone.

![Status](https://img.shields.io/badge/Status-Pending%20Meta%20API%20Approval-yellow)
![n8n](https://img.shields.io/badge/Built%20with-n8n-EA4B71?logo=n8n&logoColor=white)
![MCP](https://img.shields.io/badge/Protocol-MCP-blueviolet)
![Pinecone](https://img.shields.io/badge/Memory-Pinecone-0CF2A0)
![OpenRouter](https://img.shields.io/badge/LLM-OpenRouter-orange)
![Gemini](https://img.shields.io/badge/LLM-Gemini-4285F4?logo=google)

-----

## 🧩 What This Does

Manually responding to hundreds of Instagram DMs and comments is a full-time job. This workflow automates it intelligently:

1. Receives Instagram messages and comments via verified webhook
1. Extracts and structures message data
1. AI Agent analyzes message content using OpenRouter LLM + MCP memory
1. JavaScript intent classifier routes to the correct action path
1. Routes: Instagram reply, order processing, or escalation
1. Logs everything to Google Sheets for analytics
1. Notifies sales rep via email for high-intent messages
1. Full error handling with error logging

-----

## 🗺️ Workflow Architecture
Webhook (Instagram)
    │
    └──► Check Webhook Verification
              │
         ┌────┴────┐
       true      false
         │          │
    Extract      Respond to
    Message      Webhook
    Data
         │
         ▼
┌─── AI Customer Service Agent ──────────────────┐
│   OpenRouter Chat Model (Gemini via Router)    │
│   Simple Memory (session context)              │
│   MCP Client (Pinecone long-term memory)       │
└──────────────────┬─────────────────────────────┘
                   │
         Code in JavaScript
         (Intent Classification — Rules mode)
                   │
        ┌──────────┼──────────┐
        ▼          ▼          ▼
   Instagram    Order      Error
   Reply        Route      Route
        │          │          │
   Send Reply  Notify     Log Error
   Log to      Sales Rep  to Sheet
   Sheet       Log Order
        │
   Respond
   Success

-----

## 🛠️ Tech Stack

|Component       |Tool                   |Purpose                          |
|----------------|-----------------------|---------------------------------|
|Workflow Engine |n8n (self-hosted)      |Orchestration                    |
|LLM             |OpenRouter (Gemini)    |Long-context AI responses        |
|Long-Term Memory|MCP Client + Pinecone  |Product/brand knowledge retrieval|
|Session Memory  |Simple Memory node     |Conversation continuity          |
|Intent Routing  |JavaScript (Rules mode)|Action classification            |
|CRM Logging     |Google Sheets          |Question & order tracking        |
|Sales Alerts    |Gmail                  |High-intent lead notification    |
|Trigger         |Instagram Webhook      |Real-time message processing     |

-----

## 🤖 AI Agent Architecture

The core AI Customer Service Agent combines three memory layers:
OpenRouter Chat Model (Gemini)
    ├── Simple Memory       → remembers conversation within session
    └── MCP Client          → retrieves brand/product knowledge from Pinecone

Why Gemini? Long context window handles complex multi-turn conversations and large knowledge bases without losing context — critical for customer service scenarios.

-----

## 🔀 Intent Classification Engine

The JavaScript Intent Classifier routes each message to the right path:

|Intent                 |Action                                           |
|-----------------------|-------------------------------------------------|
|General question       |AI reply → Send Instagram response → Log to Sheet|
|Order / purchase intent|Notify Sales Rep (Gmail) → Log Order to Sheet    |
|Unrecognized / error   |Log Error to Sheet → Graceful error response     |

-----

## 🔧 Key Features

- Webhook verification — proper Meta API handshake implementation

Altayeb, [2/27/2026 4:21 AM]
- Dual-path routing — separates informational queries from sales opportunities
- Full audit trail — every interaction logged to Google Sheets
- Sales escalation — high-intent messages reach a human immediately
- Error resilience — failed requests caught, logged, and handled gracefully
- MCP Protocol — cutting-edge memory architecture for persistent context

-----

## ⚠️ Current Status

> Pending Meta API Production Access
> 
> The workflow is fully built and tested in sandbox mode. Awaiting Meta’s review and approval for Instagram Graph API production access — a standard requirement for all Instagram automation tools.
> 
> This is a Meta process limitation, not a technical one.

-----

## 🔭 Roadmap

- [ ] Meta API production approval & live deployment
- [ ] Comment auto-reply support
- [ ] Sentiment analysis for negative message escalation
- [ ] Multi-language support (Arabic/English)
- [ ] Analytics dashboard (Google Sheets → Power BI)
- [ ] WhatsApp Business API parallel deployment

-----

## 👨‍⚕️ Built By

Dr. Altayeb Almoutaz — MD turned AI Automation Engineer

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?logo=linkedin)](https://linkedin.com/in/altayeb-almoutaz-1161b9237)
[![GitHub](https://img.shields.io/badge/GitHub-Altayebalmoutaz-181717?logo=github)](https://github.com/Altayebalmoutaz)

-----

> 💡 *All test data used during development is synthetic. No real user data was processed during sandbox testing.*
