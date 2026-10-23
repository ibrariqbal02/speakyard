# Speakyard server

Language practice + entertainment app (was an Instagram clone). Express 5 + TypeScript + MongoDB (Mongoose) + Cloudinary.
Client repo: insagram-clone-client (React + Vite, folder `instagram-clone-frontend`).

## Always
- Read `docs/PROJECT_PLAN.md` first. Do the next unticked step(s) unless told otherwise.
- After finishing: tick the step, add a line to the Log, commit, push to the working branch.
- Keep the response shape `{ success, message, ... }`. Match existing code style.
- Add/adjust tests in `tests/` for every change.

## Commands
- `npm run dev` / `npm run build` / `npx tsc --noEmit`
- `npm test` (needs mongodb-memory-server download). If it can't download, most suites mock models:
  run with a temp jest config that sets `setupFilesAfterEnv: []`.

## Layout
- `src/app.ts` express app (middleware, routes) · `src/index.ts` startup
- `src/config/env.ts` env validation and config · `.env.example` all env vars
- `src/middlewares/` auth (cookie or Bearer), security (rate limits, sanitize, validation), errors
- `src/utils/authTokens.ts` cookies, token hashing, mobile token-in-body (`X-Client-Platform: mobile`)
