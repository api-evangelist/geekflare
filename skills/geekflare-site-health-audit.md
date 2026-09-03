---
name: geekflare-site-health-audit
description: Run a full website health check — uptime, load time, Lighthouse, broken links, and mixed content — with the Geekflare testing APIs.
api: Geekflare API
operations: [siteStatus, loadTime, lighthouse, brokenLink, mixedContent, redirectCheck]
generated: '2026-09-03'
method: generated
source: openapi/geekflare-openapi.json + https://docs.geekflare.com/endpoint/reference
---

# Site health audit

1. Pre-flight with `POST /up` (operationId `siteStatus`, 1 credit) to confirm the site is reachable before spending credits on heavier tests.
2. `POST /loadtime` (operationId `loadTime`, 1 credit) for full-load timing; add `targetCountries` (up to 3 ISO codes, flat 8 credits) to compare reachability from multiple regions.
3. `POST /lighthouse` (operationId `lighthouse`, 10 credits) for performance/SEO/accessibility scores — allow a 30–60s client timeout, this is a browser-based endpoint.
4. `POST /brokenlink` (operationId `brokenLink`, 2 credits) to list dead links, and `POST /mixedcontent` (operationId `mixedContent`) to find insecure HTTP resources on HTTPS pages.
5. `POST /redirectcheck` (operationId `redirectCheck`, 1 credit) to trace redirect chains with status codes for SEO and link-rot auditing.
6. Failures: 422 means the target page could not be processed (not your key); 5xx is Geekflare-side and generally not charged — check status.geekflare.com, then retry with backoff.
