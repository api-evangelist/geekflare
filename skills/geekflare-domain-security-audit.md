---
name: geekflare-domain-security-audit
description: Audit a domain's DNS, DNSSEC, TLS configuration, and open ports using the Geekflare network and security APIs.
api: Geekflare API
operations: [dnsRecord, dnsSec, tlsScan, openPorts, ping, mtr]
generated: '2026-09-03'
method: generated
source: openapi/geekflare-openapi.json + https://docs.geekflare.com/endpoint/reference
---

# Domain security audit

1. `POST /dnsrecord` (operationId `dnsRecord`, 1 credit) to pull A/AAAA/CNAME/MX/NS/TXT/CAA/SOA/SRV records — pass `types` to fetch only what you need (SPF/DKIM/DMARC live in TXT).
2. `POST /dnssec` (operationId `dnsSec`) to confirm DNSSEC validates; watch for 502/504 on slow resolvers and retry with backoff.
3. `POST /tlsscan` (operationId `tlsScan`, 1 credit) for certificate validity, issuer, expiry, and supported protocol versions — it flags deprecated SSLv2/SSLv3 support.
4. `POST /openport` (operationId `openPorts`, 2 credits; paid plans) to scan common or custom TCP port ranges; 408 means the scan timed out — narrow the range.
5. Reachability context: `POST /ping` (operationId `ping`, 2 credits, IPv4+IPv6) and `POST /mtr` (operationId `mtr`) for per-hop latency and packet loss.
6. All calls are read-only network tests — nothing to reverse; only credits are consumed, and 5xx failures are generally not charged.
