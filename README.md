# BestPick

One Cloudflare Worker: `web/` is the page, `src/worker.js` is the AI research agent at `/api/search`.
No servers, Docker or tunnels.

## Setup
1. In Cloudflare: Workers & Pages > bestpick > Settings > Variables and Secrets > add a **Secret** named `ANTHROPIC_API_KEY`.
2. Push to GitHub. Cloudflare builds and deploys. The `CACHE` KV namespace is created automatically.
3. In the Anthropic Console, set a monthly spend limit for the key.

## Optional variables (plain text)
`MODEL` (default claude-sonnet-5-5), `RATE_LIMIT` (new searches per IP per hour, default 10), `MAX_DAILY` (new searches per day, default 100).
