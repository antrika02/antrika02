<h1 align="center">Antrika Kashyap</h1>

<p align="center">
Backend & AI Systems Engineer · Computer Science, VIT Bhopal (2026)
</p>

<p align="center">
<a href="https://www.linkedin.com/in/antrika-kashyap-070502250">
<img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin"/>
</a>
<a href="mailto:antrikakashyap2@gmail.com">
<img src="https://img.shields.io/badge/Gmail-EA4335?style=for-the-badge&logo=gmail"/>
</a>
<a href="https://leetcode.com/u/antrikakashyap2/">
<img src="https://img.shields.io/badge/LeetCode-orange?style=for-the-badge&logo=leetcode"/>
</a>
<a href="https://codeforces.com/profile/antrika02">
<img src="https://img.shields.io/badge/Codeforces-blue?style=for-the-badge"/>
</a>
<a href="https://www.codechef.com/users/antrika02">
<img src="https://img.shields.io/badge/CodeChef-5B4638?style=for-the-badge&logo=codechef&logoColor=white"/>
</a>
</p>

---

## About

I build backend services and the infrastructure around LLM applications — mostly
in Python and Java, mostly with FastAPI and PostgreSQL.

The thing I find most interesting right now is **when not to call a language
model**. Most LLM systems route everything through the largest model available,
which is slow, expensive, and impossible to reproduce. I'm more interested in
systems that compute what they can deterministically, escalate only when they
genuinely need to, and can explain every decision afterwards.

---

## Currently building

**gatekeep** — *in progress, no results yet*

A library for confidence-gated cascade routing: run a cheap model first,
escalate to an expensive one only when the cheap model is genuinely unsure.

The hard part isn't the cascade — it's that raw confidence scores are poorly
calibrated, so a model reporting 90% confidence is often right far less than
90% of the time. Gating on an uncalibrated score therefore leaves real money on
the table. I'm calibrating the scores first and measuring what that's worth,
with Pareto curves across accuracy, cost, and p95 latency, and confidence
intervals on every number.

---

## Projects

### SentinelRoute
*Python · scikit-learn · Whisper · EasyOCR · GPT-4.1-mini*
[→ repository](https://github.com/antrika02/hackerrank-orchestrate-ai-router)

A multimodal message router (text, images via OCR, voice via transcription) that
classifies each incoming message as notify, digest, or mute.

The design decision worth talking about: **the language model is deliberately
kept out of the primary decision path.** Trust, history, repetition, and timing
are computed in code rather than asked of a model, security screening runs
*before* personalization so a trusted sender can't earn leniency on a scam, and
an LLM reviewer is consulted only for the genuinely ambiguous minority. The
whole pipeline runs offline and deterministically with the reviewer switched
off, which is what makes offline evaluation meaningful.

Every prediction carries a full decision trace, so any routing decision can be
audited after the fact.

### AI Documentation Assistant
*FastAPI · Qdrant · FastEmbed · Gemini · Streamlit*

A two-stage RAG pipeline that crawls technical documentation, embeds and indexes
it, and answers questions with source citations and confidence scores.
Conversation memory uses a sliding context window so follow-up questions keep
their context. Deployed on Render.

### FinPilot AI
*FastAPI · PostgreSQL · SQLAlchemy · Alembic · LangGraph*

A personal finance backend built on a layered architecture — router → service →
repository — with JWT auth, Argon2 password hashing, Pydantic v2 validation,
Alembic migrations, and ownership checks enforced in the service layer.

A LangGraph agent for natural-language financial queries is in development;
it selects tools, queries through the repository layer, and traces its reasoning
via Langfuse. No automated test suite yet — that's the next priority.

### Backend Service Platform
*Spring Boot · Redis · MySQL · Docker*

REST services with authentication, caching, and rate limiting, structured around
a clean separation between web, service, and data layers.

---

## Experience

**Software Development Intern** · Bluestock Fintech · May–Jul 2025 · Remote

Backend work on a financial analytics platform: SQL query optimisation, API
performance, and debugging production issues. Automated the deployment pipeline
with GitHub Actions, cutting deploy time from 45 minutes to 5.

---

## Competitive programming

- **LeetCode contest rating 1610** — top 22.76% globally
- **Top 10**, GeeksforGeeks institute leaderboard, VIT Bhopal
- **CodeChef 3★**
- 1,400+ problems solved across LeetCode, GeeksforGeeks, CodeChef and Codeforces
- Regular Codeforces contest participant

---

## Tools

**Languages** — Python, Java, SQL, JavaScript
**Backend** — FastAPI, Spring Boot, Node.js, SQLAlchemy, Pydantic
**Data** — PostgreSQL, MySQL, Redis, MongoDB, Qdrant, pgvector
**AI** — LangGraph, LangChain, Langfuse, RAG, Claude / OpenAI / Gemini APIs
**Infra** — Docker, GitHub Actions, Git, Linux, AWS

---

<p align="center">
Happy to talk about backend systems, LLM infrastructure, or anything involving
measuring things that people usually guess at.
</p>
