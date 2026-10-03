# BestPick

`web/` is the static site (Cloudflare Pages). `api/` is the FastAPI backend (home server + Cloudflare Tunnel).

## 1. Push to GitHub
    git init && git add . && git commit -m "BestPick first version"
    git branch -M main
    git remote add origin git@github.com:Zogsquared/bestpick.git
    git push -u origin main

## 2. Cloudflare Pages (frontend)
Workers & Pages > Create > Pages > Import an existing Git repository > pick the repo.
- Framework preset: None
- Build command: (leave blank)
- Build output directory: `web`
Every push to `main` redeploys; other branches get preview URLs.

## 3. API on the home server
1. Cloudflare Zero Trust > Networks > Tunnels > create a tunnel, copy its token.
2. Add a public hostname, e.g. `api.yourdomain.com`, pointing to `http://api:8000`.
3. `cd api && cp .env.example .env`, fill in `ANTHROPIC_API_KEY`, `GOOGLE_PLACES_API_KEY` and `YOUTUBE_API_KEY`, `TUNNEL_TOKEN`, and `ALLOWED_ORIGINS` (your Pages URL).
4. `docker compose up -d --build`

## 4. Connect them
Set `window.BESTPICK_API = "https://api.yourdomain.com"` in `web/config.js`, commit, push.
