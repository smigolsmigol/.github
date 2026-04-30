## Sibling projects

The f3d1 ecosystem:

- [`f3dx`](https://github.com/smigolsmigol/f3dx) - Rust runtime your Python imports. Drop-in for openai + anthropic SDKs with native SSE streaming, agent loop with concurrent tool dispatch, OTel emission. Includes `f3dx.cache` (content-addressable LLM response cache + tool-result memoization), `f3dx.router` (sequential / hedged-parallel LLM router), and `f3dx.fast` (CanonicalPrompt for prefix-cache hits, SpecToolDispatcher for streaming tool dispatch, budget_max_tokens hinting). `pip install f3dx`.
- [`tracewright`](https://github.com/smigolsmigol/tracewright) - Trace-replay adapter for `pydantic-evals`. Read an f3dx or pydantic-ai logfire JSONL trace, get a `pydantic_evals.Dataset`. `pip install tracewright`. The `[cache]` extra wraps candidate fns with `f3dx.cache.cached_call` so replays land in a fixture file the rest of the team can replay without an API key.
- [`pydantic-cal`](https://github.com/smigolsmigol/pydantic-cal) - Calibration metrics for `pydantic-evals`: ECE, smECE, MCE, ACE, Brier, reliability diagrams, Fisher-Rao geometry kernel. `pip install pydantic-cal`. The `[cache]` extra adds `f3dx.cache.cached_call` so a calibration dataset is recorded once and replayed forever.
- [`f3dx-bench`](https://github.com/smigolsmigol/f3dx-bench) - Public real-prod-traffic LLM benchmark dashboard. CF Worker + R2 + duckdb-wasm. [Live](https://f3dx-bench.pages.dev).
- [`llmkit`](https://github.com/smigolsmigol/llmkit) - Hosted API gateway with budget enforcement, session tracking, cost dashboards, MCP server. [llmkit.sh](https://llmkit.sh).
- [`keyguard`](https://github.com/smigolsmigol/keyguard) - Security linter for open source projects.

f3dx-cache and f3dx-router used to be separate PyPI packages; folded into f3dx on 2026-04-30 as workspace members. The old packages stay live as deprecation shims for a few months. New code: `pip install f3dx[cache,router]`.
