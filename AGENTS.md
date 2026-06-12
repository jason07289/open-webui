# Repository Guidelines

## Project Structure & Module Organization

Open WebUI combines a SvelteKit frontend with a Python backend. Frontend routes, stores, components, API clients, and i18n files live under `src/`, with static assets in `static/`. Backend code is under `backend/open_webui/`; key areas include `routers/` for FastAPI routes, `models/` for data models, `utils/` for helpers, `internal/` for persistence/config internals, and `migrations/` for Alembic migrations. Tests and fixtures are placed under `test/`. Root Docker compose files and shell helpers support local orchestration.

## Build, Test, and Development Commands

- `npm run dev`: fetches Pyodide assets and starts the Vite dev server.
- `npm run dev:5050`: starts the frontend on port 5050.
- `npm run build`: builds the frontend bundle used by the Python package.
- `npm run preview`: serves the built frontend for local inspection.
- `npm run check`: runs SvelteKit sync and TypeScript/Svelte checks.
- `npm run lint`: runs frontend ESLint, Svelte/type checks, and backend pylint.
- `npm run format` / `npm run format:backend`: format frontend files with Prettier and backend files with Ruff.
- `make install`, `make start`, `make stop`: manage the Docker Compose stack.

## Coding Style & Naming Conventions

Use TypeScript for frontend logic and Svelte components for UI. Keep component names in `PascalCase.svelte`, utility modules in descriptive `camelCase` or existing local style, and route files aligned with SvelteKit conventions. Frontend formatting is managed by Prettier and ESLint. Python targets 3.11-3.12, uses Ruff/Black-compatible formatting, 120-character lines, single quotes, and Ruff import ordering.

## Testing Guidelines

Frontend unit tests use Vitest via `npm run test:frontend`; Cypress is available with `npm run cy:open` for browser workflows. Backend test dependencies include `pytest`, `pytest-asyncio`, and `pytest-docker`; run targeted backend tests with `pytest` from the repo root after installing Python dev dependencies. Name tests by behavior and keep fixtures close to the feature area or under `test/`.

## Commit & Pull Request Guidelines

Recent history uses merge commits plus short subjects such as `refac`; prefer clearer imperative subjects, for example `Fix chat attachment cleanup`. Keep commits focused and include rationale when behavior or schema changes. Pull requests should describe the problem, summarize the solution, link issues when available, list verification commands, and include screenshots or clips for UI changes.

## Security & Configuration Tips

Do not commit secrets, databases, model files, or local state. Prefer environment variables and documented compose overrides. Review authentication, file handling, migrations, and external-provider integrations with extra care.
