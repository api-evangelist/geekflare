---
name: geekflare-grounded-web-search
description: Give an AI agent live web, news, and image search with optional AI-grounded answers via the Geekflare Search API.
api: Geekflare API
operations: [search]
generated: '2026-09-03'
method: generated
source: openapi/geekflare-openapi.json + https://docs.geekflare.com/guides/search
---

# Grounded web search for agents

1. `POST /search` (operationId `search`) on `https://api.geekflare.com` with the `x-api-key` header and `{"query": "<terms>"}`.
2. Choose the source: web, news, or image search; results come back as structured JSON (or Markdown/HTML) stripped of ads and boilerplate. Base cost 2 credits.
3. For answers instead of links, request the AI-grounded answer mode (5 credits); for full page content alongside results, use search-with-scrape (4 credits).
4. Narrow with domain filtering and time-based filtering when the agent needs fresh or site-specific results.
5. Respect the per-plan requests-per-second limit (`x-geekflare-ratelimit-second`); back off on 429 using `x-geekflare-ratelimit-reset` plus jitter.
