# Library Management Monorepo

This repo contains:
- `apps/web`: Next.js frontend (deploy on Vercel)
- `apps/api`: Flask backend (deploy on Railway)

## Local dev

### Backend (Flask)
- Create a virtualenv inside `apps/api` (recommended) and install:
  - `pip install -r requirements.txt`
- Run locally:
  - `python -m src.main` (or whatever command you use today)

### Frontend (Next.js)
From repo root:
- `npm --workspace apps/web install`
- `npm run web:dev`

Set `NEXT_PUBLIC_API_URL` to your API base, e.g. `http://localhost:5000/api`.

## Deployment

### Vercel (frontend)
- Import this repo
- Set **Root Directory** = `apps/web`
- Add env vars:
  - `NEXT_PUBLIC_API_URL` = `https://api.yourdomain.com/api`
  - `NEXTAUTH_URL` = `https://yourdomain.com`
  - `NEXTAUTH_SECRET` = (random secret)
  - `GOOGLE_CLIENT_ID`, `GOOGLE_CLIENT_SECRET`

### Railway (backend)
- Create a new service from this repo
- Set **Root Directory** = `apps/api`
- Set env vars:
  - `FRONTEND_ORIGINS` = `https://yourdomain.com,https://www.yourdomain.com`
  - `DATABASE_URL` = (Railway provides this if you add a DB)
  - `SECRET_KEY`, `JWT_SECRET_KEY`

## Domains

Simplest setup:
- `yourdomain.com` (or `www.yourdomain.com`) -> Vercel
- `api.yourdomain.com` -> Railway
