# DIRAM — Architecture & Technical Overview

## Clean Architecture Layers

DIRAM follows **Clean Architecture** principles with strict layer separation:

### Layer Responsibilities

| Layer | Responsibility | Key Components |
|-------|---------------|----------------|
| **Presentation** | User interface & API contracts | Blazor Pages, API Controllers |
| **Application** | Use cases, orchestration | Services, DTOs, Validators |
| **Domain** | Business rules & entities | Models, Aggregates, Events |
| **Infrastructure** | External integrations | DB, AI APIs, Scrapers |

## AI Integration Architecture

### Model Strategy

| Model | Use Case | Cost |
|-------|----------|------|
| DeepSeek V3 | Primary analysis & summarization | $0.38/.89 per 1M tokens |
| DeepSeek R1 (Free) | Complex reasoning & briefings | Free |
| Qwen 2.5-72B | Arabic/French multilingual processing | Low cost |

### Analysis Pipeline

```
Article Ingested → Language Detection → Preprocessing
       ↓
Morocco Relevance Scoring (0-100%)
       ↓
Sentiment Analysis (Positive/Negative/Neutral + Confidence)
       ↓
Named Entity Recognition (Countries, Officials, Organizations)
       ↓
Risk Assessment (LOW / MEDIUM / HIGH / CRITICAL)
       ↓
Alert Generation (if risk threshold exceeded)
       ↓
Dashboard Update & Notification Dispatch
```

## Database Schema (Core Entities)

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│    Articles      │     │    Analyses      │     │     Alerts      │
├─────────────────┤     ├─────────────────┤     ├─────────────────┤
│ id              │────►│ article_id       │     │ id              │
│ title           │     │ sentiment_score  │     │ title           │
│ content         │     │ risk_level       │     │ priority        │
│ source          │     │ relevance_score  │     │ alert_type      │
│ language        │     │ entities (JSON)  │     │ description     │
│ published_at    │     │ model_used       │     │ is_active       │
│ scraped_at      │     │ cost             │     │ created_at      │
└─────────────────┘     └─────────────────┘     └─────────────────┘

┌─────────────────┐     ┌─────────────────┐
│     Users        │     │   User Roles    │
├─────────────────┤     ├─────────────────┤
│ id              │     │ ADMIN           │
│ username        │     │ ANALYST         │
│ email           │     │ VIEWER          │
│ role            │     │ GUEST           │
│ is_active       │     └─────────────────┘
│ last_login      │
└─────────────────┘
```

## API Endpoints Overview

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/users/login | Authenticate user |
| GET | /api/articles/ | List articles (paginated) |
| POST | /api/articles/upload | Upload & analyze article |
| POST | /api/analysis/analyze-article | AI analysis of article |
| POST | /api/analysis/intelligence-briefing | Generate AI briefing |
| GET | /api/alerts/ | Get active alerts |
| POST | /api/alerts/ | Create alert |
| GET | /api/analysis/health | AI service health check |
| GET | /api/analysis/usage-stats | AI cost & usage stats |

## Deployment Architecture

```
                    ┌─────────────────┐
                    │   NGINX Proxy    │
                    │   (Port 80/443)  │
                    └────────┬────────┘
                             │
              ┌──────────────┼──────────────┐
              ▼              ▼              ▼
     ┌────────────┐  ┌────────────┐  ┌────────────┐
     │  Frontend   │  │  Backend   │  │  Scraper   │
     │  Blazor     │  │  FastAPI   │  │  Service   │
     │  :5000      │  │  :8000     │  │  (cron)    │
     └────────────┘  └─────┬──────┘  └────────────┘
                           │
                    ┌──────┴──────┐
                    │  Database   │
                    │  SQLite /   │
                    │  PostgreSQL │
                    └─────────────┘
```

## Cost Management

- Daily AI budget cap: **$25 USD**
- Automatic switch to free models when budget approaches limit
- Per-request cost tracking and reporting
- Monthly usage analytics and optimization recommendations
