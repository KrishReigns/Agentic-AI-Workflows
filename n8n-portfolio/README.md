# 🤖 Agentic AI & Automation Workflows — n8n Portfolio

**Sai Krishna Kandula** | Senior Cloud & DevOps Engineer | GenAI Automation Specialist  
📧 krishna1996sai@gmail.com | 📍 Worcester, MA | [LinkedIn](#)

---

## Overview

This repository showcases a collection of **production-grade agentic AI and automation workflows** built using **n8n**, **AWS Bedrock**, **Azure OpenAI**, and modern LLM integrations. These workflows demonstrate real-world applications of GenAI for business process automation, SRE operations, and intelligent data pipelines.

These projects directly complement 7+ years of hands-on cloud and DevOps engineering experience across AWS, Azure, and Kubernetes — and reflect expertise in integrating AI/LLM platforms into operational workflows.

---

## 🗂️ Workflow Portfolio

| # | Workflow | Stack | Complexity | Category |
|---|----------|-------|------------|----------|
| 1 | [Client Onboarding Workflow](#1-client-onboarding-workflow) | JotForm · HubSpot · Gmail · Telegram | ⭐⭐⭐⭐ | Business Automation |
| 2 | [Email Personal Assistant](#2-email-personal-assistant) | OpenRouter LLM · Google Docs · Drive | ⭐⭐⭐⭐ | GenAI Agent |
| 3 | [Inventory Check Automation](#3-inventory-check-automation) | AWS Bedrock · Google Sheets · Gmail | ⭐⭐⭐ | AI + SRE Ops |
| 4 | [Table Booking Bot](#4-table-booking-bot) | AWS Bedrock · Google Sheets · Chat UI | ⭐⭐⭐ | Conversational AI |
| 5 | [Sales Email Automation Assistant](#5-sales-email-automation-assistant) | LLM · Gmail · CRM | ⭐⭐⭐⭐⭐ | GenAI Sales Ops |
| 6 | [Trend Watcher](#6-trend-watcher) | Web Scraping · LLM · Notifications | ⭐⭐⭐⭐ | AI Research Agent |
| 7 | [Daily Bean Feedback](#7-daily-bean-feedback) | Forms · Sentiment AI · Sheets | ⭐⭐⭐ | AI Analytics |
| 8 | [HTTP Request / API Integration](#8-http-request--api-integration) | OpenAI API · REST · File Export | ⭐⭐ | API Automation |

---

## Workflow Details

### 1. Client Onboarding Workflow

**📁 [`workflows/client-onboarding/`](./workflows/client-onboarding/)**

An end-to-end automated client onboarding pipeline that triggers from a JotForm submission and orchestrates a full multi-day nurture sequence.

**Architecture:**
```
JotForm Trigger → Validation (IF node) → HubSpot CRM Contact Creation
    ↓                                              ↓
Telegram Alert (error)              Team Notification (Telegram)
                                               ↓
                                    Welcome Email (Gmail)
                                               ↓
                                    Wait 2 Hours
                                               ↓
                                    Download PDF Guide (Google Drive)
                                               ↓
                                    Send PDF Guide Email
                                               ↓
                                    Wait 1 Day → VIP Offer Email
                                               ↓
                                    Wait 2 Days → Onboarding Complete Email
                                               ↓
                                    HubSpot Status Update → Telegram Gift Alert
```

**Key Features:**
- ✅ Input validation with error alerting via Telegram
- ✅ Automatic HubSpot CRM contact creation and lifecycle status management
- ✅ 3-stage timed email drip sequence (Welcome → PDF Guide → VIP Offer → Completion)
- ✅ Google Drive PDF attachment delivery
- ✅ Real-time team Telegram notifications at key milestones

**Tech Stack:** `n8n` · `JotForm` · `HubSpot CRM` · `Gmail` · `Google Drive` · `Telegram Bot API`

---

### 2. Email Personal Assistant

**📁 [`workflows/email-personal-assistant/`](./workflows/email-personal-assistant/)**

An AI-powered writing assistant with a web chat interface that intelligently routes requests to specialized writing tools and auto-saves approved content to Google Docs.

**Architecture:**
```
Chat Trigger (Web UI) → AI Assistant Agent (OpenRouter LLM)
                                    ↓
              ┌─────────────────────┼─────────────────────┐
              ↓                     ↓                     ↓
    Sales Letter Writer      Cold Email Writer      Google Docs Tool
    (AIDA Structure)         (150 words + CTA)      (Auto-save on approve)
              └─────────────────────┼─────────────────────┘
                                    ↓
                          JavaScript Output Cleaner
                                    ↓
                            Clean Response to User
```

**Key Features:**
- ✅ Intelligent intent routing — automatically selects the right writing tool
- ✅ AIDA-structured long-form sales letter generation
- ✅ Short cold email generation (≤150 words + CTA enforcement)
- ✅ Session memory (20-message context window)
- ✅ "Approve" command triggers auto-save to Google Docs with timestamp
- ✅ Google Drive file management integration

**Tech Stack:** `n8n` · `OpenRouter LLM` · `LangChain Agent` · `Google Docs` · `Google Drive` · `Memory Buffer`

---

### 3. Inventory Check Automation

**📁 [`workflows/inventory-check-automation/`](./workflows/inventory-check-automation/)**

A weekly scheduled AI agent that monitors inventory levels, identifies low-stock items, and automatically sends formatted alert emails — powered by AWS Bedrock.

**Architecture:**
```
Schedule Trigger (Every Monday 9AM)
        ↓
Google Sheets (Read Inventory Data)
        ↓
Filter (Stock < Threshold)
        ↓
Aggregate (Combine all low-stock items)
        ↓
AWS Bedrock AI Agent (DeepSeek v3)
        ↓
Gmail Tool → Auto-send Low Stock Alert Email
```

**Key Features:**
- ✅ Fully automated weekly inventory monitoring — zero manual effort
- ✅ AWS Bedrock (DeepSeek v3.2) for intelligent alert message generation
- ✅ Dynamic threshold comparison per item
- ✅ AI-generated structured alert with supplier reorder recommendations
- ✅ Handles out-of-stock edge cases with special messaging

**Tech Stack:** `n8n` · `AWS Bedrock (DeepSeek v3.2)` · `Google Sheets` · `Gmail` · `LangChain AI Agent`

> 💡 **SRE Relevance:** This pattern directly mirrors production alert automation — replacing inventory with infrastructure metrics (CPU, memory, disk) gives you an AI-powered ops alerting system.

---

### 4. Table Booking Bot

**📁 [`workflows/table-booking-bot/`](./workflows/table-booking-bot/)**

A conversational AI booking agent with a live chat UI that handles restaurant reservations, checks for conflicts in real time, and prevents double bookings — powered by AWS Bedrock.

**Architecture:**
```
Chat UI (Public Web Interface)
        ↓
AI Agent (AWS Bedrock — DeepSeek v3.2)
        ↓
    ┌───┴───┐
    ↓       ↓
Read     Add Booking
Bookings  (if no conflict)
(Google   (Google Sheets)
Sheets)
```

**Key Features:**
- ✅ Natural language booking — understands free-form input
- ✅ Real-time conflict detection — prevents double bookings
- ✅ Google Sheets as live booking database
- ✅ Persistent conversation memory (20-message window)
- ✅ Polite conflict resolution — suggests alternative slots
- ✅ Public-facing chat UI — no installation required

**Tech Stack:** `n8n` · `AWS Bedrock (DeepSeek v3.2)` · `Google Sheets` · `LangChain Agent` · `Chat Trigger`

---

### 5. Sales Email Automation Assistant

**📁 [`workflows/sales-email-automation/`](./workflows/sales-email-automation/)**

A multi-agent sales automation system that combines lead research, personalized email generation, and CRM updates into a single intelligent workflow.

**Key Features:**
- ✅ 24-node complex multi-agent orchestration
- ✅ Personalized outreach email generation at scale
- ✅ CRM integration for lead tracking
- ✅ Automated follow-up sequencing

**Tech Stack:** `n8n` · `LLM APIs` · `Gmail` · `CRM Integration` · `LangChain`

---

### 6. Trend Watcher

**📁 [`workflows/trend-watcher/`](./workflows/trend-watcher/)**

An AI research agent that monitors industry trends, scrapes relevant sources, summarizes insights using LLMs, and delivers curated briefings automatically.

**Key Features:**
- ✅ 34-node autonomous research pipeline
- ✅ Web data collection and aggregation
- ✅ LLM-powered trend summarization and insight extraction
- ✅ Automated delivery of curated intelligence reports

**Tech Stack:** `n8n` · `Web Scraping` · `LLM APIs` · `Notification Services`

---

### 7. Daily Bean Feedback

**📁 [`workflows/daily-bean-feedback/`](./workflows/daily-bean-feedback/)**

An automated customer feedback collection and AI sentiment analysis pipeline for a restaurant, feeding insights into a structured reporting dashboard.

**Key Features:**
- ✅ Automated feedback ingestion from form submissions
- ✅ AI sentiment analysis on customer responses
- ✅ Structured data storage in Google Sheets
- ✅ Operational reporting for business insights

**Tech Stack:** `n8n` · `Google Sheets` · `AI Sentiment Analysis` · `Forms`

---

### 8. HTTP Request / API Integration

**📁 [`workflows/http-request/`](./workflows/http-request/)**

A lightweight workflow demonstrating direct OpenAI REST API integration with automated text-to-file conversion — useful as a template for custom LLM API integrations.

**Key Features:**
- ✅ Direct REST API call to OpenAI endpoint
- ✅ Structured request/response handling
- ✅ Automatic file conversion and export

**Tech Stack:** `n8n` · `OpenAI API` · `HTTP Request` · `File Conversion`

> ⚠️ **Note:** Replace `YOUR_OPENAI_API_KEY` in the workflow JSON with your own key before running.

---

## 🛠️ Tech Stack Summary

| Category | Technologies |
|----------|-------------|
| **Automation Platform** | n8n (self-hosted & cloud) |
| **AI / LLM** | AWS Bedrock (DeepSeek v3.2), OpenRouter, OpenAI API, LangChain Agents |
| **Cloud** | AWS (Bedrock, IAM), Google Cloud (Sheets, Docs, Drive, Gmail) |
| **CRM & Forms** | HubSpot, JotForm |
| **Messaging** | Telegram Bot API, Gmail |
| **Memory & State** | LangChain Memory Buffer Window |
| **Languages** | JavaScript (n8n Code nodes), JSON |

---

## 🔗 Connection to Cloud & DevOps Work

These workflows extend my core cloud engineering expertise into **GenAI-powered automation**:

| n8n Workflow Pattern | Cloud/DevOps Equivalent |
|----------------------|------------------------|
| Inventory Check + AWS Bedrock alerts | CloudWatch + AI-powered incident triage |
| Client Onboarding drip sequence | GitOps deployment pipeline with staged rollouts |
| Table Booking conflict detection | Distributed lock management in microservices |
| Email Assistant with memory | Stateful LLM agents for SRE runbook automation |
| Trend Watcher research agent | Automated threat intelligence & log analysis |

---

## 🚀 How to Use These Workflows

1. **Install n8n** — [n8n.io](https://n8n.io) (cloud or self-hosted via Docker)
2. **Import a workflow** — Open n8n → Workflows → Import from File → select `workflow.json`
3. **Configure credentials** — Replace all `YOUR_CREDENTIAL_ID` placeholders with your own API keys and OAuth connections
4. **Activate** — Toggle the workflow to active and test

```bash
# Quick self-hosted n8n setup via Docker
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -v n8n_data:/home/node/.n8n \
  docker.n8n.io/n8nio/n8n
```

---

## 📄 License

MIT License — feel free to use, modify, and build upon these workflows.

---

*Part of the professional portfolio of **Sai Krishna Kandula** — Senior Cloud & DevOps Engineer specializing in AWS, Azure, Kubernetes, Terraform, and GenAI automation.*
