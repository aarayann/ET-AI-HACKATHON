<div align="center">

# Finshala

**AI-powered financial wellness for India's 150M+ retail investors.**

*Economic Times GenAI Hackathon 2026 — Finance & Fintech Track*

[![Demo](https://img.shields.io/badge/▶_Demo-Watch_Now-8B6F47?style=for-the-badge)](https://youtu.be/EZbtbZWgScs)
&nbsp;
[![React](https://img.shields.io/badge/React_18-61DAFB?style=flat-square&logo=react&logoColor=black)](https://react.dev)
[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://typescriptlang.org)
[![Python](https://img.shields.io/badge/Python_3.11-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![Flask](https://img.shields.io/badge/Flask-000000?style=flat-square&logo=flask)](https://flask.palletsprojects.com)
[![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?style=flat-square&logo=supabase&logoColor=white)](https://supabase.com)

</div>

---

## What is Finshala?

A personal financial advisor costs ₹25,000–₹50,000/year. Generic apps give the same advice to everyone. **Finshala does neither.**

It combines deterministic computation engines (for accurate math) with AI agents (for personalized explanation) — giving every Indian investor advice that was previously only available to the wealthy.

> **Core principle: LLMs explain. They never calculate.**
> All tax math, SIP projections, and Monte Carlo simulations run through deterministic Python engines. AI only generates the narrative — no hallucinated numbers.

---

## Features

### 🔥 FIRE Path Planner
Month-by-month retirement projections across three scenarios — Lean, Regular, and Fat FIRE — with age-based asset allocation, SIP breakdowns by fund type, and milestone tracking up to age 85.

### 💯 Money Health Score
A 0–900 score across 6 weighted dimensions: emergency preparedness, insurance coverage, investment diversification, debt health, tax efficiency, and retirement readiness. Each dimension returns specific findings and ranked action items.

### 🧾 Tax Wizard
Upload your Form 16 PDF (including password-protected). Finshala extracts your salary and deductions, compares Old vs New regime tax, finds unused 80C/80D/NPS deductions, and explains the recommendation in plain language.

### 🧠 AI Shala — Multi-Agent Pipeline

Five specialized agents run sequentially on your profile:

```
Tax Agent → XAI Agent → FIRE Agent → Stress Agent → GenUI Agent
```

| Agent | What it does |
|-------|-------------|
| Tax Agent | Calculates both regimes, calls LLM to explain the delta |
| XAI Agent | Runs health score, builds a SHAP-style waterfall decomposition |
| FIRE Agent | Generates Lean / Regular / Fat projections (pure deterministic) |
| Stress Agent | LLM generates 3 Indian crisis scenarios → 5,000 Monte Carlo runs each |
| GenUI Agent | Assembles a dynamic dashboard schema from all results |

**Example SHAP output:**
```
Base score (population avg):  480 / 900
  + Tax Efficiency            +58  ← your strongest area
  + Debt Health               +42
  − Emergency Fund            −72  ← only 1.4 months covered
  − Insurance Coverage        −61  ← no life insurance
  ─────────────────────────────────
  Your score:                 424 / 900  (Fair)
```

### 💬 AI Chatbot
Conversational assistant for Indian tax and investment questions. Runs Ollama locally (`llama3.1:8b`) with automatic fallback to HuggingFace inference if Ollama isn't available.

### 📄 PDF Reports
Server-generated branded reports via ReportLab — FIRE roadmap, Tax comparison, and Health Score breakdown. Download and share offline.

---

## Tech Stack

| Layer | Technologies |
|-------|-------------|
| Frontend | React 18, TypeScript, Vite 5, Tailwind CSS, shadcn/ui, Framer Motion, Three.js, Recharts |
| Backend (Node.js) | Express 4 — LLM proxy gateway |
| Backend (Python) | Flask 3.1, pdfplumber, pikepdf, ReportLab, NumPy, httpx |
| AI / LLM | Ollama (llama3.1:8b), HuggingFace Inference API, Meta Llama 3.1 8B, Phi-3.5 Mini |
| Auth & DB | Supabase |

---

## Project Structure

```
finshala/
├── frontend/               # React + Vite app
│   └── src/
│       ├── pages/          # FIRE, Health, Tax Wizard, AI Shala
│       ├── components/     # UI components + GenUIRenderer
│       ├── services/       # Computation engines (TypeScript)
│       └── hooks/          # useAuth, useUserProfile
│
└── backend/
    ├── server.js           # Node.js — LLM proxy (Express)
    └── python_api/         # Flask — all financial engines
        ├── app.py
        ├── fire_engine.py
        ├── health_score_engine.py
        ├── report_generator.py
        └── ai_shala/
            ├── orchestrator.py
            ├── llm_client.py
            └── agents/     # tax, xai, stress, genui
```

---

## Running Locally

**Prerequisites:** Node.js 20+, Python 3.11+, and optionally [Ollama](https://ollama.ai)

```bash
# Clone
git clone https://github.com/aarayann/finshala.git
cd finshala

# Frontend
cd frontend && npm install && npm run dev

# Node.js backend
cd ../backend && npm install && node server.js

# Python backend
cd python_api && pip install -r requirements.txt && python app.py

# (Optional) Ollama chatbot
ollama pull llama3.1:8b && ollama serve
```

Copy `.env.example` to `.env` in `backend/` and fill in your `HUGGINGFACE_API_KEY` and Supabase credentials.

**API health checks:**
```bash
curl http://localhost:3000/api/health   # Node.js
curl http://localhost:5000/api/health   # Flask
curl http://localhost:5000/api/v2/ai-shala/health
```

---

## Impact

| Who | Problem solved | Estimated saving |
|-----|---------------|-----------------|
| Salaried professional (₹8–15 LPA) | Wrong tax regime + missed deductions | ₹25,000–₹65,000/year |
| Young investor (25–35) | No FIRE plan or emergency fund | ₹10L+ corpus started |
| Family with loans | Unaware of 36% credit card cost | ₹12,000–₹40,000/year |
| Mid-career (35–45) | Inadequate insurance | ₹5–30L medical risk covered |

~40 million Indians file the wrong tax regime every year. Average overpayment: ₹25,000–₹60,000.

---

## Team

| Name | LinkedIn |
|------|----------|
| Aryan Chauhan | [aarayann](https://www.linkedin.com/in/aarayann/) |
| Bhavya Sodhi | [bhavya-sodhi](https://www.linkedin.com/in/bhavya-sodhi-7a60372bb/) |
| Harsh Mittal | [harshm1111](https://www.linkedin.com/in/harshm1111/) |
| Härshit Bhalia | [härshit-bhalia](https://www.linkedin.com/in/h%C3%A4rshit-bhalia-76319128a/) |

---

<div align="center">

Built with ❤️ for India's financial future &nbsp;·&nbsp; ET GenAI Hackathon 2026

</div>
