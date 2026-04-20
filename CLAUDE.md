# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Workflow Rules

- After modifying any code, always run `git commit` and `git push` to the current working branch. This is required for backup purposes.
- After developing a new feature, run `npm run build` and check for errors. Fix all errors before committing and pushing.

## Project

**SmartNewsLetter** — an AI-powered newsletter platform built with Next.js 14 (App Router) as part of the YuvAI course. Located in `SmartNewsLetter/`.

## Commands

All commands run from the `SmartNewsLetter/` directory.

```bash
npm run dev          # Start development server (http://localhost:3000)
npm run build        # Production build — must pass before every commit
npm run lint         # Lint the codebase
npx prisma migrate dev   # Apply database migrations
npx prisma studio        # Open Prisma GUI to inspect the database
```

## Tech Stack

| Layer | Technology |
|-------|------------|
| Framework | Next.js 14 App Router |
| Language | TypeScript |
| Styling | Tailwind CSS |
| Database | PostgreSQL via Prisma ORM |
| Auth | NextAuth.js |
| AI | Anthropic Claude API |
| Email | Resend |
| Deployment | Vercel |

## Required Environment Variables

```env
DATABASE_URL=
NEXTAUTH_SECRET=
NEXTAUTH_URL=
ANTHROPIC_API_KEY=
RESEND_API_KEY=
```

Copy `.env.example` to `.env.local` and fill in values before running the app.

## Architecture

The app uses the **Next.js 14 App Router**. Key architectural concerns:

- **AI summaries**: Claude API is called server-side (Route Handlers or Server Actions) to summarize and categorize articles. Never call the Anthropic API from client components.
- **Email delivery**: Resend sends newsletters; email templates should be React components rendered server-side.
- **Auth**: NextAuth.js guards admin routes. Subscriber management (subscribe/unsubscribe) is public-facing.
- **Database**: Prisma schema is the source of truth for data models. Always run `npx prisma migrate dev` after schema changes and commit the generated migration files.
- **Scheduling**: Automated newsletter delivery is triggered via Vercel Cron Jobs (configured in `vercel.json`).
