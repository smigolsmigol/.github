## f3d1

Rust runtime + dashboard ecosystem for Python AI apps. Open source, MIT. Solo project by Federico Benini, building in public.

### currently shipping

- **[f3dx](https://github.com/smigolsmigol/f3dx)** - the Rust runtime your Python imports. Drop-in for openai + anthropic SDKs with native SSE streaming + concurrent tool dispatch + OTel emission. `pip install f3dx`.
- **[f3dx-bench](https://github.com/smigolsmigol/f3dx-bench)** - the first prod-traffic latency dashboard for LLMs. Real telemetry from f3dx + llmkit users who opt in. Live at [f3dx-bench.pages.dev](https://f3dx-bench.pages.dev).
- **[llmkit](https://github.com/smigolsmigol/llmkit)** - hosted API gateway with budget enforcement + cost dashboards + MCP server. Live at [llmkit.sh](https://llmkit.sh).

### the f3d1 ecosystem

| Repo | What |
|---|---|
| [f3dx](https://github.com/smigolsmigol/f3dx) | Rust runtime your Python imports. Native SSE + agent loop + OTel + MCP + bundled cache + router + 4 inference-acceleration pillars under `f3dx.fast`. `pip install f3dx`. |
| [tracewright](https://github.com/smigolsmigol/tracewright) | Trace-replay adapter for `pydantic-evals`. Logfire JSONL -> Dataset. `pip install tracewright`. |
| [pydantic-cal](https://github.com/smigolsmigol/pydantic-cal) | Calibration metrics for `pydantic-evals`. ECE / smECE / MCE / ACE / Brier / reliability diagrams + Fisher-Rao geometry. `pip install pydantic-cal`. |
| [f3dx-bench](https://github.com/smigolsmigol/f3dx-bench) | Public real-prod-traffic LLM benchmark dashboard. CF Worker + R2 + duckdb-wasm. |
| [llmkit](https://github.com/smigolsmigol/llmkit) | Hosted gateway: budgets, cost dashboards, MCP, audit. TS on Cloudflare Workers. |
| [keyguard](https://github.com/smigolsmigol/keyguard) | Security linter for open source projects. Finds and fixes what others only report. |
| [.github](https://github.com/smigolsmigol/.github) | Org-level substrate: SECURITY/CODE_OF_CONDUCT/CONTRIBUTING + reusable security/scorecard/release-please/dependabot-automerge workflows. |

### f3dx.fast (since 0.0.19, 2026-04-30)

Four primitives in the f3dx wheel that cut closed-API spend on long agentic loops. `CanonicalPrompt` keeps the static prefix bytes-identical so OpenAI's prefix cache fires from turn two onwards (we measure 91% hit rate and 28.6% input cost cut on a 3-turn loop vs the same workload built naively). `cache_tool_call` memoizes safe tools across the loop; a 50KB `Read` lands in 42us instead of 9.4ms, a `gh run list` cached at 30s TTL drops from 702ms to 6us. `budget_max_tokens` reads prior-turn observations and caps `max_tokens` at p99 + 20%; on runaway-prone prompts that's ~94% off the upper bound. `SpecToolDispatcher` runs side-effect-free tools as soon as their streamed arguments parse cleanly, in parallel with the rest of the response stream; on a synthetic 3-tool turn that drops 1.6s to 1.0s. The ICLR 2026 oral on this is arXiv:2510.04371.

f3dx-cache and f3dx-router used to be separate packages; folded into f3dx as workspace members on the same date. Old PyPI packages stay live as deprecation shims for a few months. New code: `pip install f3dx[cache,router]`.

### contact

- email: smigolsmigol@protonmail.com
- security disclosures: see SECURITY.md
- general support: see [SUPPORT.md](https://github.com/smigolsmigol/.github/blob/main/SUPPORT.md)
