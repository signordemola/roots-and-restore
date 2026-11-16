# Roots & Restore

The starting point for a booking and practice system for a wellness studio with several practitioners.

![Roots & Restore starter page](docs/screenshot.png)

## The problem

A wellness studio with several practitioners often runs on separate tools for booking, client forms and payouts.
This project plans to put booking, health intake forms, session notes and practitioner payouts in one place.

## Features

This repo is at the setup stage. Today it has:

- A Next.js App Router project with TypeScript in strict mode.
- Tailwind CSS 4 and shadcn/ui, with one `Button` component.
- Light and dark themes. Press `d` to switch.
- ESLint, Prettier and a type-check script.

No booking features are built yet.

## Tech stack

- Next.js 16 and React 19
- TypeScript
- Tailwind CSS 4
- shadcn/ui on Base UI
- pnpm

## Run locally

You need:

- Node.js 20.9 or later (the minimum for Next.js 16)
- pnpm 12

```bash
pnpm install
pnpm dev
```

Open `http://localhost:3000`.

This app needs no environment variables yet.

### Other commands

```bash
pnpm typecheck   # TypeScript check
pnpm lint        # ESLint
pnpm build       # production build
```

## Status and what's next

Early setup. Only the starter page exists.

Planned next:

- Database schema and sign-in with roles for owner, practitioner and client.
- Online booking across several practitioners.
- Health intake form and liability waiver before a first visit.
- Session notes for practitioners.
- Owner dashboard with revenue and commission for each practitioner.

---

Built by [Adedamola](https://github.com/signordemola) · [Demola Studio](https://www.demolastudio.com)

See also: [booking-engine](https://github.com/signordemola/booking-engine)
