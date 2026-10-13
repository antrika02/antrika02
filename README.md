<h1 align="center">Antrika Kashyap</h1>

<p align="center">
Backend & AI Systems Engineer · B.Tech Computer Science, VIT Bhopal (2026)
</p>

<p align="center">
<a href="https://antrika-portfolio.vercel.app">
<img src="https://img.shields.io/badge/Portfolio-000000?style=for-the-badge&logo=vercel"/>
</a>
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

I build backend services and the infrastructure around LLM applications, mostly
in Python and Java, mostly with FastAPI, Spring Boot and PostgreSQL.

Two things I care about most:

- **Systems that stay correct under load.** My Java order platform sold exactly
  100 of 100 units when 100 customers ordered at the same moment.
- **Knowing when not to call a language model.** Most LLM systems send everything
  to the biggest model available, which is slow, expensive and impossible to
  reproduce. I prefer systems that compute what they can in plain code, ask a
  model only when they genuinely need to, and can explain every decision
  afterwards.

---

## Currently building

**gatekeep** (*in progress, no results yet*)

A library for confidence-gated cascade routing: run a cheap model first,
escalate to an expensive one only when the cheap model is genuinely unsure.

The hard part isn't the cascade. Raw confidence scores are poorly calibrated, so
a model reporting 90% confidence is often right far less than 90% of the time,
and gating on an uncalibrated score leaves real money on the table. I'm
calibrating the scores first and measuring what that's worth, with Pareto curves
across accuracy, cost and p95 latency, and confidence intervals on every number.

Also learning: Microsoft Azure Fundamentals (AZ-900), in progress.

---

## Projects

### Smart Order Processing Platform
*Java 21 · Spring Boot · MySQL · Redis · Docker · Flyway*
[→ repository](https://github.com/antrika02/Smart_Order_Processing_Platform)

An order backend built to survive many customers buying the same item at once.
Row-level locking and idempotency keys stop overselling and double-processing:
in a test with **100 simultaneous orders against 100 units, 0 were oversold**.

Layered design (controller, service, repository), JWT auth with role-based
access, Flyway-versioned MySQL schemas and 11 REST endpoints. **30 automated
tests at 85% coverage**, run in CI.

### SentinelRoute
*Python · scikit-learn · Whisper · EasyOCR · GPT-4.1-mini*
[→ repository](https://github.com/antrika02/hackerrank-orchestrate-ai-router)

Built for HackerRank's Orchestrate hackathon. A multimodal message router (text,
images via OCR, voice via transcription) that classifies each incoming message
as notify, digest or mute, in a 13-module pipeline.

The design decision worth talking about: **the language model is deliberately
kept out of the primary decision path.** Trust, history, repetition and timing
are computed in code rather than asked of a model, security screening runs
*before* personalization so a trusted sender can't earn leniency on a scam, and
an LLM reviewer is consulted only for the genuinely ambiguous minority. The
whole pipeline runs offline and deterministically with the reviewer switched
off, which is what makes offline evaluation meaningful.

Every prediction carries a full decision trace, so any routing decision can be
audited after the fact. A separate evaluation suite documents known failure
modes.

### FinPilot AI
*FastAPI · PostgreSQL · SQLAlchemy · Alembic · LangGraph · Langfuse · AWS EC2*
[→ repository](https://github.com/antrika02/finance_assistant)

A personal finance backend (transactions, budgets, analytics, PDF/CSV reports)
with 30+ REST endpoints on a router, service, repository architecture. JWT auth,
Argon2 password hashing, Pydantic v2 validation, Alembic migrations, and
ownership checks enforced in the service layer on every record.

A LangGraph agent answers natural-language financial questions by selecting
backend tools and querying through the repository layer; its tool calls, token
use and latency are traced with Langfuse. Deployed on AWS EC2, with **128 tests
covering 91% of the code**, run in CI on every push.

### AI Documentation Assistant
*FastAPI · Qdrant · FastEmbed · Firecrawl · Gemini 2.5 Flash*
[→ repository](https://github.com/antrika02/AI-Documentation-Assistant)

A two-stage RAG pipeline that crawls technical documentation, embeds and indexes
it, and answers questions with source citations and a confidence score.
Conversation memory uses a sliding context window so follow-up questions keep
their context. Includes `/health` and `/metrics` endpoints, request-timing
middleware and an evaluation harness (dataset, runner, metrics report) added
through a feature branch and pull request.

### AI Guest Messaging Automation
*FastAPI · React · PostgreSQL · Claude API*
[→ repository](https://github.com/antrika02/AI_messaging_automation)

Classifies guest messages and drafts replies with the Claude API, then applies
confidence guardrails: **90%+ auto-sends, 60 to 89% goes to a human for review,
under 60% escalates.** Every decision is stored in PostgreSQL as an audit trail.
Deployed on Render and Vercel. Built as a working demo; it has not been connected
to a real hospitality client.

---

## Experience

**Software Development Intern** · Bluestock Fintech · May to Jul 2025 · Remote

Backend work on a live fintech analytics platform with 2,000+ daily active users,
in Agile sprints with product and QA teams.

- Cut query latency by 38% and raised peak throughput by 30% by profiling a
  recurring slowdown and redesigning the indexing and query strategy.
- Refactored 10+ REST API endpoints for consistent contracts and predictable
  error handling.
- Resolved 15+ production incidents independently, from root cause to verified fix.
- Automated the release pipeline with GitHub Actions and Docker, cutting
  deployment time from 45 minutes to 5.

---

## Competitive programming

- **LeetCode:** 1,487 problems solved (393 Easy, 942 Medium, 152 Hard), contest
  rating **1758**, top **10.37%** globally, 138-day maximum streak
- **CodeChef:** 4★, max rating **1852**, global rank 2,716, 21 contests; scored
  84% on the CodeChef Java Skill Assessment
- **Codeforces:** Pupil, max rating 1300
- **Top 10**, GeeksforGeeks institute leaderboard, VIT Bhopal

---

## Tools

**Languages** — Java, Python, C++, SQL, JavaScript
**Backend** — Spring Boot, Spring Security, FastAPI, SQLAlchemy, Pydantic, JWT
**Data** — PostgreSQL, MySQL, Redis, Qdrant, Flyway, Alembic
**AI** — LangGraph, Langfuse, RAG, Claude / OpenAI / Gemini APIs
**Testing & Infra** — JUnit 5, Testcontainers, pytest, JaCoCo, Docker, GitHub Actions, AWS EC2, Linux, Git

---

<p align="center">
Happy to talk about backend systems, LLM infrastructure, or anything involving
measuring things that people usually guess at.
</p>
