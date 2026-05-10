# Boilerplate — Full-Stack AI Chat Starter Template

A production-ready full-stack boilerplate for building AI chat applications. Ships with user authentication, subscription management, admin panel, OpenAI chat integration, and multi-provider OAuth — all wired up and ready to extend.

---

## Overview

Skip weeks of setup. This boilerplate gives you a complete foundation for any AI-powered SaaS product: secure auth with 2FA, Stripe subscriptions with multiple plans, OpenAI chat with per-user token tracking, a role-based admin panel, dynamic theming, and a clean three-layer backend architecture. Just configure your `.env`, plug in your AI logic, and ship.

---

## What's Included

### Authentication & Security
- JWT authentication via secure httpOnly cookies (access + refresh tokens)
- Two-factor authentication — email (HOTP) and app-based (TOTP)
- OAuth 2.0 — Google, Microsoft, and Meta (Facebook) sign-in
- CSRF protection, rate limiting (SlowAPI), session management
- Role-based access control — `user` and `admin` roles

### Subscriptions & Payments
- Stripe integration — products, pricing plans, subscriptions
- Subscription lifecycle via Stripe webhooks
- Per-plan token limits for AI usage
- Payment and refund tracking

### AI Chat
- OpenAI integration with configurable model, base URL, and API version
- Token usage tracked per message and per user
- Conversation history with full chat message persistence
- Rate limits and token limits enforced per subscription plan

### Admin Panel
- User management — view, edit, suspend accounts
- Site settings — dynamic configuration without redeployment
- Subscription and payment oversight
- Structured JSON logging (production) / colored console (development)

### Frontend
- Dynamic theming via React Context
- Automatic token refresh on 401 — transparent to the user
- Typed API hooks with TanStack React Query for server state
- Route guards for auth protection and role-based access

---

## Tech Stack

**Backend**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?style=flat&logo=postgresql&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat&logo=openai&logoColor=white)

**Frontend**

![React](https://img.shields.io/badge/React_19-20232A?style=flat&logo=react&logoColor=61DAFB)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=flat&logo=typescript&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_v4-38B2AC?style=flat&logo=tailwind-css&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat&logo=vite&logoColor=white)

| Layer | Technology |
|---|---|
| Backend | Python FastAPI |
| Database | PostgreSQL (SQLAlchemy 2.0 + Alembic) |
| AI | OpenAI (configurable base URL) |
| Auth | JWT (httpOnly cookies), 2FA, OAuth |
| Payments | Stripe |
| Email | Azure Communication Services |
| Frontend | React 19 + TypeScript + TailwindCSS v4 |
| Build Tool | Vite |
| State (server) | TanStack React Query |
| State (client) | Redux Toolkit + React Context |
| Containerization | Docker + Docker Compose |

---

## Backend Architecture

Three-layer pattern per module — clean, testable, consistent:

```
routes.py       ← FastAPI endpoints, request/response models
service.py      ← Business logic, exception handling
repository.py   ← Database queries (SQLAlchemy ORM)
schemas.py      ← Pydantic validation models
```

**Modules included:** auth, users, oauth, subscriptions, stripe, payments, products, conversations, chat\_messages, openai, twofactor, admin, site\_settings, config, token\_limits

---

## Quick Start

```bash
# Clone and configure
cp .env.example .env
# Fill in: DATABASE_URL, TOKEN_SECRET, STRIPE_*, OPENAI_API_KEY, GOOGLE_*, AZURE_*

# Start with Docker (recommended)
docker compose up

# Or run manually
pip install -r requirements.txt
alembic upgrade head
uvicorn app.main:app --reload --port 8000

# Frontend
cd frontend && npm install && npm run dev
```

---

## Built By

Open for use as a starting template for AI SaaS projects.
