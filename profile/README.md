## f3d1

Rust runtime + dashboard ecosystem for Python AI apps. Open source, MIT. Solo project by Federico Benini, building in public.

### currently shipping

- **[f3dx](https://github.com/smigolsmigol/f3dx)** - the Rust runtime your Python imports. Drop-in for openai + anthropic SDKs with native SSE streaming + concurrent tool dispatch + OTel emission. `pip install f3dx`.
- **[f3dx-bench](https://github.com/smigolsmigol/f3dx-bench)** - the first prod-traffic latency dashboard for LLMs. Real telemetry from f3dx + llmkit users who opt in. Live at [f3dx-bench.pages.dev](https://f3dx-bench.pages.dev).
- **[llmkit](https://github.com/smigolsmigol/llmkit)** - hosted API gateway with budget enforcement + cost dashboards + MCP server. Live at [llmkit.sh](https://llmkit.sh).

### the f3d1 ecosystem

| Repo | What |
|---|---|
| [f3dx](https://github.com/smigolsmigol/f3dx) | Rust runtime your Python imports. Native SSE + agent loop + OTel + MCP. |
| [tracewright](https://github.com/smigolsmigol/tracewright) | Trace-replay adapter for `pydantic-evals`. Logfire JSONL -> Dataset. |
| [f3dx-cache](https://github.com/smigolsmigol/f3dx-cache) | Content-addressable LLM response cache + replay. redb + RFC 8785 JCS + BLAKE3. |
| [pydantic-cal](https://github.com/smigolsmigol/pydantic-cal) | Calibration metrics for `pydantic-evals`. ECE / MCE / ACE / Brier / reliability diagrams + Fisher-Rao geometry. |
| [f3dx-router](https://github.com/smigolsmigol/f3dx-router) | In-process Rust LLM router. Sequential + hedged-parallel. Composes with llmkit. |
| [f3dx-bench](https://github.com/smigolsmigol/f3dx-bench) | Public real-prod-traffic LLM benchmark dashboard. CF Worker + R2 + duckdb-wasm. |
| [llmkit](https://github.com/smigolsmigol/llmkit) | Hosted gateway: budgets, cost dashboards, MCP, audit. TS on Cloudflare Workers. |
| [keyguard](https://github.com/smigolsmigol/keyguard) | Security linter for open source projects. Finds and fixes what others only report. |

### security advisories

- [GHSA-g6fx-g2jr-hvmf](https://github.com/pydantic/logfire/security/advisories/GHSA-g6fx-g2jr-hvmf) - Logfire scrubber JSON-decode bypass (Apr 2026, credit accepted)

### contact

- email: smigolsmigol@protonmail.com
- security disclosures: see SECURITY.md
- general support: see [SUPPORT.md](https://github.com/smigolsmigol/.github/blob/main/SUPPORT.md)
