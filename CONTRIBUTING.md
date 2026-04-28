# Contributing

Thanks for considering a contribution to the f3d1 ecosystem.

## Default flow

1. Open an issue describing what you want to change BEFORE coding (especially for non-trivial changes - it saves both sides time).
2. Fork the repo, branch from `main`, push your work to the fork.
3. Open a PR against `main`. Use the PR template.
4. CI must pass: tests, linting, security scans (gitleaks + semgrep + cargo-audit / pip-audit / npm-audit), scorecard.
5. One reviewer (Federico). Expect a response within 7 days. Quiet weeks happen.

## Voice + style rules

These apply to ALL prose that ships in the repo (READMEs, commit messages, PR bodies, doc files, blog drafts):

- **WHY-led, not WHAT-led.** READMEs lead with the punchline + why-this-exists, then quick-start, then architecture. Linus's git README, Karpathy's nanoGPT README, and Bryan Cantrill's repos are the references.
- **No AI-spam phrases.** Banned: "comprehensive", "robust", "seamless", "leverages", "in today's fast-paced", "cutting-edge", "powerful", "delve", "dive deep", "unleash". Strip these before submitting.
- **ASCII only.** No em-dashes (use `-`), no en-dashes (use `-`), no smart quotes (use `"`/`'`), no arrows (use `->`/`<-`), no ellipsis (use `...`).
- **No bullet-walls.** Bullets are for lists, not paragraphs. Three sentences is usually better than four bullets.
- **Source claims.** "Faster" needs a number. "More secure" needs a CVE / advisory link. "Used by N" needs N.

## Commit message style

- Subject: lowercase, imperative, under 70 chars. Examples: `fix bench TIME_WAIT rebind on macOS`, `feat: f3dx.bench opt-in telemetry SDK`.
- Body: explain WHY (not just WHAT - the diff already shows what). Connect to the issue / advisory / regression that prompted the change.
- No "Co-Authored-By: Claude" trailers. No emoji unless there's a strong reason.

## Code style

- **Python**: ruff format + ruff check, mypy where types are non-trivial. Pre-commit config provided.
- **Rust**: cargo fmt + cargo clippy with `-D warnings`. SHA-pinned actions for everything.
- **TypeScript**: biome check + biome format. tsc --noEmit on every push.
- **Tests**: required for new functionality. Bug fixes need a regression test.

## Security

If you found a vulnerability, do NOT open a public issue. Use the private disclosure flow described in [SECURITY.md](SECURITY.md).

## License

By contributing you agree that your contribution will be licensed under the same MIT license as the project.

## Questions

Open a [discussion](https://github.com/smigolsmigol/.github/discussions) or email smigolsmigol@protonmail.com.
