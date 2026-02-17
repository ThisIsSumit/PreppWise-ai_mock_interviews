# Prepwise — AI Mock Interviews

Prepwise is a **Next.js 15 + React 19** app for running **AI-powered mock interviews**. It combines a modern UI (Tailwind + Radix UI), form handling (React Hook Form + Zod), and integrations for **voice/agent experiences (Vapi)** and **Firebase** (client + admin) to help users practice interview questions in a realistic way.

---

## Tech Stack

- **Framework:** Next.js `15.5.x` (App Router) + React `19`
- **Language:** TypeScript
- **UI:** Tailwind CSS, Radix UI, lucide-react icons
- **Forms & Validation:** react-hook-form, zod, @hookform/resolvers
- **Date utilities:** dayjs
- **Notifications:** sonner
- **AI / Agent tooling:** `@vapi-ai/web`, `ai`, `@ai-sdk/google`
- **Data/Auth:** `firebase`, `firebase-admin`

---

## Project Structure (high level)

```plain text
app/
  (auth)/            # auth-related routes/layouts
  (root)/            # main application routes/layouts
  api/vapi/generate/ # server route for Vapi-related generation
components/
  ui/                # shared UI primitives
  *.tsx              # app components (forms, cards, agent UI, etc.)
lib/
  actions/           # server/client actions (auth/general)
  utils.ts           # shared helpers
  vapi.sdk.ts        # Vapi SDK wrapper/config
firebase/            # Firebase configuration/helpers
types/               # TypeScript type definitions
public/              # static assets
```


---

## Getting Started

### 1) Install dependencies

```shell script
npm install
```


### 2) Configure environment variables

Create a `.env.local` file in the project root.

Use placeholders (don’t commit real secrets). Your exact keys may vary depending on how Firebase/Vapi/Google AI are configured in your project, but typically you’ll want something like:

```shell script
# App
NEXT_PUBLIC_APP_URL=http://localhost:3000

# Firebase (client)
NEXT_PUBLIC_FIREBASE_API_KEY=YOUR_VALUE_HERE
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=YOUR_VALUE_HERE
NEXT_PUBLIC_FIREBASE_PROJECT_ID=YOUR_VALUE_HERE
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=YOUR_VALUE_HERE
NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=YOUR_VALUE_HERE
NEXT_PUBLIC_FIREBASE_APP_ID=YOUR_VALUE_HERE

# Firebase Admin (server)
FIREBASE_ADMIN_PROJECT_ID=YOUR_VALUE_HERE
FIREBASE_ADMIN_CLIENT_EMAIL=YOUR_VALUE_HERE
FIREBASE_ADMIN_PRIVATE_KEY=YOUR_VALUE_HERE

# Vapi
NEXT_PUBLIC_VAPI_PUBLIC_KEY=YOUR_VALUE_HERE
VAPI_API_KEY=YOUR_VALUE_HERE

# Google AI (if used via @ai-sdk/google)
GOOGLE_GENERATIVE_AI_API_KEY=YOUR_VALUE_HERE
```


Notes:
- Variables prefixed with `NEXT_PUBLIC_` are exposed to the browser.
- Keep server-only secrets (admin keys, private keys) **without** `NEXT_PUBLIC_`.

### 3) Run the dev server

```shell script
npm run dev
```


Open: **http://localhost:3000**

---

## Scripts

```shell script
npm run dev     # Start Next.js in dev mode (Turbopack)
npm run build   # Production build
npm run start   # Start the production server
npm run lint    # Run linting
```


---

## Features (typical flow)

- **Authentication** (via Firebase)
- **Mock interview sessions** with an AI agent experience (Vapi integration)
- **Structured forms** for collecting interview preferences/details (React Hook Form + Zod)
- **Reusable UI components** for consistent styling and behavior
- **API route(s)** under `app/api/*` for server-side operations (e.g., generation/agent setup)

---

## Deployment

This is a standard Next.js app and can be deployed to platforms like **Vercel**.

Before deploying:
- Add all required environment variables in your hosting provider’s settings.
- Ensure Firebase Admin credentials are configured as server-side secrets.
- Run a production build locally to verify:

```shell script
npm run build
npm run start
```


---

## Contributing

1. Create a feature branch
2. Keep changes focused and well-described
3. Run `npm run lint` before opening a PR

---

## License

Add your license here (e.g., MIT) or state “All rights reserved” if you don’t want redistribution.