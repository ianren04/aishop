# Progress

## 2026-03-30

### Completed

- Reviewed repository docs, backend services, frontend flow, sample data, and tests for interview-report extraction.
- Counted repository-level report metrics: `100` product samples, `4` query samples, `4` expected ranking samples, `3` contract tests, and `2` backend endpoints.
- Added `docs/AI_导购项目技术报告.md` for direct interview presentation, with tables, Mermaid flowcharts, score-weight charts, and screenshot placeholders.

### Verification

- Report content only uses facts that exist in the repository, docs, or code.
- Business metrics not present in the repository were explicitly excluded from the results section.

## 2026-03-23

### Completed

- Read and structured the scope, flow, fields, and module boundaries from `MVP_PRD.md`.
- Confirmed the repository initially only contained planning documents and no implementation.
- Added `docs/` for scope freeze, schema, model contract, backend rules, API contract, and validation plan.
- Added `data/` for product samples, query samples, and expected ranking samples.
- Added `backend/` with FastAPI app, Pydantic models, mock parser, filtering and ranking logic, and contract tests.
- Added `frontend/` with React + Vite single-page MVP for input, clarification, results, and error states.
- Installed frontend dependencies and verified a production build succeeds.
- Installed backend dependencies and verified contract tests pass.
- Wired Volcengine Ark configuration through root `.env` and added Ark Responses API client and parser path.
- Verified the live Ark-backed parser path can be invoked from the backend service.

### Current Focus

- The mock end-to-end MVP is implemented and verified locally.
- The Ark-backed parser is connected; the next step is improving prompt quality and adding stricter output normalization.

### Pending Next Actions

1. Tighten the Ark prompt so constraints like repair rejection and accessory requirements are extracted more reliably.
2. Add response normalization and fallback repair logic for partially correct model outputs.
3. Add more ranking regression cases and clarification edge cases.

### Known Blockers

- The current runtime environment required elevated execution for Python commands and frontend build subprocesses.
- The live Ark parser currently reaches the API but still misses some user constraints in first-pass parsing, so prompt tuning is still needed.
