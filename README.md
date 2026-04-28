# f3d1 org defaults

Org-level default community files + reusable workflows for the [f3d1 ecosystem](https://github.com/smigolsmigol). Github auto-uses files in this magic `.github` repo as defaults for any f3d1 repo that doesn't override them.

## What's here

| File | Used as |
|---|---|
| `profile/README.md` | The f3d1 / profile landing page at github.com/smigolsmigol |
| `SECURITY.md` | Default disclosure policy across all f3d1 repos |
| `CODE_OF_CONDUCT.md` | Contributor Covenant 2.1 default |
| `CONTRIBUTING.md` | Default contribution flow + voice/style rules |
| `SUPPORT.md` | Where to ask for help |
| `CITATION.cff` | Academic citation template |
| `.github/FUNDING.yml` | Sponsorship channels |
| `.github/ISSUE_TEMPLATE/` | Bug / feature / security templates + config |
| `.github/PULL_REQUEST_TEMPLATE.md` | Default PR template |
| `.github/workflows/security-rust-py.yml` | Reusable: gitleaks + semgrep + cargo-audit + pip-audit (for Rust+PyO3 repos) |
| `.github/workflows/security-python.yml` | Reusable: gitleaks + semgrep + ruff + bandit + mypy + pip-audit |
| `.github/workflows/security-typescript.yml` | Reusable: gitleaks + semgrep + npm audit |
| `.github/workflows/scorecard.yml` | Reusable: OpenSSF Scorecard with SARIF upload |

## Override semantics

Any consumer repo can ship its own copy of any of these files; the per-repo file overrides the org-level default. Use the override sparingly - the point of this repo is uniform baseline.

## How consumer repos call the reusable workflows

Each f3d1 repo's local `.github/workflows/security.yml` is a 5-line shim:

```yaml
name: security
on:
  push: { branches: [main] }
  pull_request: { branches: [main] }
  workflow_dispatch:
jobs:
  call:
    uses: smigolsmigol/.github/.github/workflows/security-rust-py.yml@main
```

(Swap `security-rust-py.yml` for `security-python.yml` / `security-typescript.yml` per repo language.) Same shape for `scorecard.yml`.

When this repo updates a SHA pin or adds a new tool to one of the reusable workflows, every consumer picks up the change at next CI run. Single source of truth.

## Future additions (planned)

- `.github/workflows/release-please.yml` - reusable release automation (Phase 4)
- `configs/pre-commit-{rust-py,python,typescript}.yaml` - shared pre-commit hooks (Phase 3)
- `.github/workflows/dependabot-automerge.yml` - auto-merge patch + minor Dependabot bumps when CI green (Phase 5)

## License

MIT.
