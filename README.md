# SmartNewsLetter

An AI-powered newsletter platform that curates, summarizes, and delivers personalized news digests to subscribers — built as part of the YuvAI Next.js course.

## Purpose

SmartNewsLetter automates the process of gathering news from various sources, uses AI to summarize and categorize articles, and sends beautifully formatted email newsletters to subscribers based on their interests and preferences.

## Features

- AI-generated article summaries using the Claude API
- Topic-based personalization for each subscriber
- Automated newsletter scheduling and delivery
- Subscription management (subscribe / unsubscribe)
- Admin dashboard to manage topics, sources, and send history

## Tech Stack

| Layer | Technology |
|-------|------------|
| Framework | [Next.js 14](https://nextjs.org/) (App Router) |
| Language | TypeScript |
| Styling | Tailwind CSS |
| Database | PostgreSQL via [Prisma ORM](https://www.prisma.io/) |
| Authentication | [NextAuth.js](https://next-auth.js.org/) |
| AI / LLM | [Anthropic Claude API](https://www.anthropic.com/) |
| Email Delivery | [Resend](https://resend.com/) |
| Deployment | [Vercel](https://vercel.com/) |

## Getting Started

```bash
# Install dependencies
npm install

# Set up environment variables
cp .env.example .env.local

# Run database migrations
npx prisma migrate dev

# Start the development server
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

## Environment Variables

```env
DATABASE_URL=
NEXTAUTH_SECRET=
NEXTAUTH_URL=
ANTHROPIC_API_KEY=
RESEND_API_KEY=
```

## License

MIT
