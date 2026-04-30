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

### f3dx.fast inference acceleration (2026-04-30)

Four shipped pillars in `f3dx==0.0.19`, all real-API validated against OpenAI gpt-4o-mini, all reproducible from committed fixtures (`F3DX_BENCH_OFFLINE=1` for replay without an API key):

- `f3dx.fast.CanonicalPrompt` - prefix-cache canonicalization. **91.1% OpenAI cache hit rate, 28.6% real input cost reduction** vs naive baseline (3-turn agentic loop head-to-head).
- `f3dx.fast.SpecToolDispatcher` - speculative tool execution with threaded fire (Sutradhara streaming JSON parser, ICLR 2026 oral). **37% wall-clock cut** on a synthetic 3-tool agentic turn.
- `f3dx.cache.cache_tool_call` - tool-result memoization with FileWitness / TTLWitness invalidation. **223x file Read, 111,415x gh CLI** (eliminates 702ms subprocess cost per cached call).
- `f3dx.fast.budget_max_tokens` - token budget hinting from prior-turn observations. **94% headroom saved** on runaway-prone prompts.

`f3dx-cache` and `f3dx-router` consolidated into the f3dx wheel on the same date; old PyPI packages stay resolvable as deprecation shims for 4-6 months. New code uses `pip install f3dx[cache,router]` and imports from `f3dx.cache` / `f3dx.router`.

### contact

- email: smigolsmigol@protonmail.com
- security disclosures: see SECURITY.md
- general support: see [SUPPORT.md](https://github.com/smigolsmigol/.github/blob/main/SUPPORT.md)
