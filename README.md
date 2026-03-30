# AI Switch Shopping MVP

This repository contains a local MVP for a second-hand Nintendo Switch shopping assistant.

## Stack

- Backend: Python + FastAPI + Pydantic
- Frontend: React + Vite
- Local / remote LLM parsing: Volcengine Ark Responses API or mock fallback

## Structure

- `docs/`: scope, schema, rules, contracts, validation plan
- `data/`: product samples, query samples, expected rankings
- `backend/`: API, parser, ranking rules, tests
- `frontend/`: single-page MVP UI

## Environment

The backend reads environment variables from the repository root `.env`.

Example:

```bash
LLM_MODE=ark
LLM_BASE_URL=https://ark.cn-beijing.volces.com/api/v3
LLM_MODEL=doubao-seed-2-0-mini-260215
ARK_API_KEY=...
```

## Backend

Install:

```bash
pip install -r backend/requirements.txt
```

Run:

```bash
uvicorn backend.app.main:app --reload
```

## Frontend

Install:

```bash
cd frontend
npm install
```

Run:

```bash
npm run dev
```

## Notes

- `LLM_MODE=ark` uses Volcengine Ark Responses API.
- If the remote LLM call fails, the backend falls back to the mock parser so the local MVP remains usable.
- The current ranking logic still uses heuristic scoring over local sample data.
