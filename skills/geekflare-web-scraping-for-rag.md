---
name: geekflare-web-scraping-for-rag
description: Turn any web page into LLM-ready Markdown or structured JSON for RAG ingestion using the Geekflare Web Scraping API.
api: Geekflare API
operations: [webScrape, metaScrape]
generated: '2026-09-03'
method: generated
source: openapi/geekflare-openapi.json + https://docs.geekflare.com/guides/web-scraping
---

# Web scraping for RAG and LLM context

1. Authenticate every call with the `x-api-key` header against `https://api.geekflare.com` (get a free key with 500 credits/month at auth.geekflare.com/register).
2. `POST /webscraping` (operationId `webScrape`) with `{"url": "<target>"}`. JavaScript rendering is automatic — the API fetches without a browser first and falls back to rendering only when needed. Request Markdown output for token-efficient LLM context.
3. For blocked pages, set `proxyMode: "auto"` (retry through a proxy only when blocked; proxy adds 4 credits) and consider stealth mode for CAPTCHA-protected targets.
4. For structured fields, use CSS/XPath extraction or `extractionMode: "template"` with the ready-made `product` or `contact` templates.
5. When you only need page metadata (title, description, Open Graph, JSON-LD), use `POST /metascraping` (operationId `metaScrape`, 2 credits) instead of scraping the full DOM.
6. Cost control: webScrape is 1 credit; watch `x-geekflare-credits-remaining` on every response and stop before 402. Retry only 429/5xx, honoring `x-geekflare-ratelimit-reset` — retries re-run the request and consume credits again (no idempotency keys).
