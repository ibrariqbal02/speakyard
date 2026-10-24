# Speakyard: commands for the coding assistant (VS Code)

## One-time setup on your computer

```bash
git clone https://github.com/ibrariqbal02/speakyard.git
cd speakyard
cd backend && npm install && cp .env.example .env && cd ..           # then fill backend/.env
cd frontend/speakyard-frontend && npm install && cp .env.example .env && cd ../..
code .
```

## How every command works

1. In the terminal: `git checkout release-dev && git pull`
2. Paste the command. It works on a new `feature/...` branch and pushes it.
3. Test with the checklist it gives you.
4. On GitHub open a pull request `feature/...` → `release-dev` and merge it.
5. When `release-dev` is tested on the dev server, open a pull request `release-dev` → `release-prod-sp`.

Run one command at a time, and only one assistant session at a time.

## C1. UX pass, English only
```
Speakyard: on branch feature/ux-pass from release-dev, do the UX pass:
English only (onboarding asks native language, English level A1-C2, goal). Remove all Instagram leftovers
(collapsed icon sidebar, Instagram icon, texts, blue). Bottom tab bar under 768px. Home = practice dashboard
(greeting, daily goal ring, streak, Talk to AI card, Practice with a person card, topic of the day with 3
phrases, online people to practice with). Profile = learner profile (level badge, native language, goal,
country, bio, stats), no posts grid/saved/archive. Messages header + empty state fixed. Skeletons, toasts,
empty/error states, dark mode, 360px to desktop. Login/register in Speakyard style.
Add step 2.3b to the plan and tick it. Push the branch.
```

## C2. Safety + admin panel (1.20–1.22, 2.18–2.21)
Needs: your admin email in `backend/.env` as `ADMIN_EMAILS=you@example.com`.
```
Speakyard: on branch feature/admin-safety from release-dev, do steps 1.20-1.22 and 2.18-2.21.
Report and block work from profile, chat and call screens. When an ADMIN_EMAILS user logs in,
show an Admin link and open /admin (separate admin layout, desktop first, works on mobile).
Push the branch.
```

## C3. Real chat, complete
```
Speakyard: on branch feature/chat from release-dev, make chat production quality:
sent/delivered/seen ticks, typing and online status, unread badges in nav and list, reply to a message,
emoji reactions, delete for me/for everyone, edit, images and voice notes with upload progress,
infinite scroll with cursor pagination (1.15 for messages), new-message sound and browser notification
when the tab is hidden, search conversations, group chats (create, rename, add/remove members, admins).
Blocked users cannot message. Push the branch.
```

## C4. HD audio/video calls + group calls (2.9–2.15)
Needs: LiveKit Cloud project → `LIVEKIT_URL`, `LIVEKIT_API_KEY`, `LIVEKIT_API_SECRET` in `backend/.env`.
```
Speakyard: on branch feature/calls from release-dev, do steps 2.9-2.15 with LiveKit.
1-to-1 audio and video calls from chat and profile, group calls from group chats (up to 8).
Incoming call screen with ringtone (works on any page), accept/decline, busy, missed call, timeout.
HD: 720p (1080p when bandwidth allows) with simulcast and adaptive stream; audio with echo cancellation,
noise suppression and auto gain. Call screen: mute, camera on/off, switch camera, speaker, screen share
on desktop, network quality, reconnecting state, timer, topic card, report/block.
Call history and rating. "Practice now" random matching. Push the branch.
```

## C5. AI calls (2.4–2.8)
Needs: Anthropic API key and a speech key (e.g. Deepgram) in `backend/.env`.
```
Speakyard: on branch feature/ai-calls from release-dev, do steps 2.4-2.8.
AI call screen should feel like a phone call. English only. Push the branch.
```

## C6. Streaks + notifications (2.16–2.17)
```
Speakyard: on branch feature/streaks from release-dev, do steps 2.16-2.17. Push the branch.
```

## C7. Production setup + deploy (rest of Phase 1)
Needs: Render, Vercel, MongoDB Atlas (two databases: dev and prod), Sentry.
```
Speakyard: on branch feature/production from release-dev, do the remaining Phase 1 steps
(1.7, 1.14-1.19, 1.23-1.28). Two environments:
dev = release-dev → dev.speakyard.net + api-dev.speakyard.net,
prod = release-prod-sp → speakyard.net + api.speakyard.net.
CI runs on every PR. Give me the exact DNS records for Wix and every env var for Render and Vercel. Push the branch.
```

## C8. Mobile app (Phase 3), on the `mobile` branch
Needs: Android Studio.
```
Speakyard: on branch mobile, do Phase 3. Create mobile/ with Capacitor (app id net.speakyard.app) using the
frontend build, mic/camera permissions, calls working in the app, push notifications with Firebase,
app icon and splash. Give me the steps to run on my phone and build a signed .aab. Push the branch.
```

## C9. Play Store (Phase 4)
```
Speakyard: help me with Phase 4. Write the privacy policy, terms and delete-account pages,
store listing text, and Data safety answers. Push the branch.
```

## Short commands
- `Speakyard: show plan status`
- `Speakyard: fix this bug: <what you saw>`
