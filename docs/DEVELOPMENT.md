# Speakyard development guide

Speakyard is a web + mobile app for practicing spoken English with real people (chat, audio/video/group calls)
and with an AI partner. It started as an Instagram clone; old post/reel code is kept but hidden.

## Repo layout

| Folder | What | Stack |
|---|---|---|
| `backend/` | API + Socket.IO server | Express 5, TypeScript, MongoDB (Mongoose), Cloudinary |
| `frontend/speakyard-frontend/` | Web app (also wrapped for mobile) | React 19, Vite, TypeScript, Tailwind, React Query |
| `mobile/` | Android/iOS shell (Capacitor), added on the `mobile` branch | Capacitor |
| `docs/` | Plan, commands, this guide | |

## Branches and release flow

```
feature/<name> ──PR──> release-dev ──PR (tested)──> release-prod-sp
mobile (mobile work) ──PR──> release-dev
```

- `release-dev`: integration/staging. All work lands here first via pull request. Deploys to the dev environment.
- `release-prod-sp`: production. Only updated by a pull request from `release-dev` after testing. Never commit directly.
- `mobile`: mobile app work until it is merged into `release-dev`.
- Start every task from the latest `release-dev`: `git checkout release-dev && git pull && git checkout -b feature/<name>`.

## Working rules (for people and coding assistants)

- Read `docs/PROJECT_PLAN.md` first. Do the requested step(s), or the next unticked one.
- After finishing: tick the step, add a line to the plan's Log, commit, push the feature branch, open a PR to `release-dev`.
- Never push to `release-prod-sp` directly. Never commit secrets; keep `.env.example` files up to date.
- Keep API responses shaped `{ success, message, ... }`. Match existing code style.
- Add or update tests for every change. Run build + tests for every part you changed.
- Do not add AI-tool names, co-author lines or session links to commits, PRs or files.
- End each task with a short manual test checklist for the owner.

## Commands

Backend (`backend/`):
- `npm run dev` · `npm run build` · `npx tsc --noEmit` · `npm test`
- Tests use mongodb-memory-server. If it cannot download, most suites mock models: run with a temporary
  jest config that sets `setupFilesAfterEnv: []`.

Frontend (`frontend/speakyard-frontend/`):
- `npm run dev` · `npm run build` · `npm run lint` · `npm test`

## Key files

- Backend: `src/app.ts` (middleware, routes) · `src/index.ts` (startup, HTTP + Socket.IO) · `src/socket/` ·
  `src/config/env.ts` (env validation) · `src/middlewares/` (auth cookie or Bearer, rate limits, sanitize, errors) ·
  `src/utils/authTokens.ts` (cookies, token hashing, mobile tokens via `X-Client-Platform: mobile`)
- Frontend: `src/api/axios.ts` (API client, token refresh) · `src/lib/socket.ts` · `src/hooks/` · `src/services/` ·
  `src/pages/` · `src/components/`
