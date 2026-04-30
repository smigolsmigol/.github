## Sibling projects

The f3d1 ecosystem:

- [`f3dx`](https://github.com/smigolsmigol/f3dx) - Rust runtime your Python imports. Drop-in for openai + anthropic SDKs with native SSE streaming, agent loop with concurrent tool dispatch, OTel emission. Bundles `f3dx.cache` (content-addressable LLM response cache, redb + JCS + BLAKE3) + `f3dx.router` (in-process LLM router, hedged-parallel) + `f3dx.fast` (4 inference-acceleration pillars, 28.6% real OpenAI cost cut measured). `pip install f3dx`.
- [`tracewright`](https://github.com/smigolsmigol/tracewright) - Trace-replay adapter for `pydantic-evals`. Read an f3dx or pydantic-ai logfire JSONL trace, get a `pydantic_evals.Dataset`. `pip install tracewright`. `[cache]` extra wires `f3dx.cache.cached_call` for fixture-backed real-API candidate runs.
- [`pydantic-cal`](https://github.com/smigolsmigol/pydantic-cal) - Calibration metrics for `pydantic-evals`: ECE, smECE, MCE, ACE, Brier, reliability diagrams, Fisher-Rao geometry kernel. `pip install pydantic-cal`. `[cache]` extra wires `cached_call` for one-time-spend calibration datasets.
- [`f3dx-bench`](https://github.com/smigolsmigol/f3dx-bench) - Public real-prod-traffic LLM benchmark dashboard. CF Worker + R2 + duckdb-wasm. [Live](https://f3dx-bench.pages.dev).
- [`llmkit`](https://github.com/smigolsmigol/llmkit) - Hosted API gateway with budget enforcement, session tracking, cost dashboards, MCP server. [llmkit.sh](https://llmkit.sh).
- [`keyguard`](https://github.com/smigolsmigol/keyguard) - Security linter for open source projects. Finds and fixes what others only report.

`f3dx-cache` and `f3dx-router` were standalone packages until 2026-04-30; now consolidated into the f3dx wheel as Cargo workspace members + Python sub-modules. Old PyPI packages remain as deprecation shims for 4-6 months; new code uses `pip install f3dx[cache,router]` and imports from `f3dx.cache` / `f3dx.router`.
