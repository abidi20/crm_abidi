# Interaction & Messaging Backend (Node.js + Express + PostgreSQL)

## Quick start
1. **Create `.env`** (copy from `.env.example`) and fill your PostgreSQL connection info.
2. Install deps: `npm install`
3. Initialize DB: `npm run db:setup`
4. (Optional) Seed demo data: `npm run db:seed`
5. Start in dev: `npm run dev`

## Environment
See `.env.example` for required variables.

## Endpoints (selection)
- **Auth**
  - `POST /auth/register` — body: `{ name, email, password }`
  - `POST /auth/login` — body: `{ email, password }` → returns JWT
- **Users**
  - `GET /users` (auth)
  - `GET /users/:id` (auth)
  - `PUT /users/:id` (auth, self or admin)
  - `DELETE /users/:id` (admin)
- **Interactions**
  - `POST /interactions` (auth)
  - `GET /interactions` (auth; optional query `participantId`)
  - `GET /interactions/:id` (auth)
  - `POST /interactions/:id/participants` (auth) — add participant
- **Messages**
  - `GET /interactions/:id/messages` (auth)
  - `POST /interactions/:id/messages` (auth) — body: `{ body }`

> This is a compact but production-style structure: controllers in routes, pg pooled client, JWT auth middleware, and SQL schema in `sql/schema.sql`.
