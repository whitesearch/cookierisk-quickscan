---
name: cookierisk-quickscan
description: Check one public website homepage for cookies and tracking observed before banner interaction using CookieRisk QuickScan. Use when the user asks for a pre-interaction cookie or tracking check on a specific public homepage.
---

# CookieRisk QuickScan

Use the CookieRisk MCP server at `https://cookierisk.eu/mcp` via Streamable HTTP. It requires no CookieRisk account. If the tools are unavailable in this client, direct the user to the [connection instructions](https://cookierisk.eu/developers/mcp).

1. Use the public HTTP(S) homepage the user asked to scan. Submit only the origin with an optional trailing slash. If the user gave a deeper URL, ask whether to check its homepage. Keep credentials, paths, query strings, fragments, and private URLs out of the request.
2. Call `start_quickscan` once with `{"url":"https://example.com/"}`, substituting the approved homepage. This can start a scan that visits the website. If the response indicates reuse, report the capture time and cooldown end when the server provides them. If a start request fails or its outcome is unclear, surface the error. For `domain_limit`, explain that the domain is in cooldown. Use `domainCooldownEndsAt` when supplied. Treat `retryAfter` as a minimum wait for another request, without promising that the domain cooldown ends then. A second start requires a fresh user request.
3. Keep the returned `scanId`. Wait at least `pollAfterSeconds` before calling `get_quickscan_result` with that ID and between pending reads. For a temporary read error with `retryAfter`, wait that many seconds before resuming. If the scan stays pending beyond the time available, give the user the scan ID and last known state so they can resume without starting another scan.
4. Prefer the tool's structured result. On completion, summarize the observed cookies, tracking signals, or banner evidence the result actually contains. Note reuse when applicable. If a report URL is present, treat it as a link anyone with the URL can open. For failed, missing, or incomplete results, report the state and any available evidence limits. Keep unknowns separate from findings.

This is a point-in-time baseline for one homepage. Keep conclusions limited to the recorded pre-interaction observations. Accept and reject behavior, other pages, ongoing monitoring, and legal determinations are outside this workflow.
