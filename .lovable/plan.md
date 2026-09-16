# Import genie-friend-buddy into this project

The GitHub project is public and already built on the same stack as this one, so the import is a straight copy plus backend setup.

## What the app is

A YouTube content studio: you add competitor channels and source videos, the app analyses them with AI, generates ideas and scripts, and helps you assemble and schedule videos.

Screens being brought over:
- Landing page
- Sign up / sign in
- App home (dashboard)
- Channels
- Sources (per-video analysis with progress)
- Chat (AI assistant)
- Studio (video editor and assembly)

## Steps

1. Copy the full codebase from GitHub into this project: all pages, components, AI and YouTube logic, styling, and dependencies.
2. Turn on Lovable Cloud so the app has a database, user accounts, and server-side AI.
3. Recreate the database: profiles, projects, sources, ideas, scripts, videos — including access rules so each person only sees their own data.
4. Re-create the scheduled-video background job endpoint.
5. Verify: the app builds, every page loads, sign-up and sign-in work, and one create/read flow saves and reads back real data.

## Notes

- Existing data from the other project is not copied — this starts with an empty database. If you want the old records, export them and I will import them.
- AI features run through Lovable's built-in AI, so no API keys are needed from you.
- The original project noted one limitation it could not solve: final video rendering (captions, music, effects) happens in the browser during assembly, because the hosting runtime has no video encoder. That limitation carries over.

## Technical details

- Source repo: `bestmarket/genie-friend-buddy` (public, TanStack Start + Tailwind v4 + shadcn, Supabase-backed).
- Copy `src/`, `public/`, `drizzle/`, `supabase/migrations/`, config files; merge `package.json` dependencies (ai SDK, streamdown, motion, recharts, etc.) and install.
- Enable Lovable Cloud, then replay the 7 SQL migrations in timestamp order plus the two drizzle migrations if they add anything not already covered; confirm GRANTs and RLS on every public table.
- Keep `src/routes/_authenticated/route.tsx` as the auth gate; protected loaders stay under that subtree.
- `src/lib/ai.server.ts` reads `LOVABLE_API_KEY` from the server env — provided automatically.
- Public webhook stays at `src/routes/api/public/hooks/scheduled-videos.ts`.
