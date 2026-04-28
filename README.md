# smigolsmigol/.github

Org-level default community files for [smigolsmigol](https://github.com/smigolsmigol). Github auto-uses files in this magic repo as defaults for any repo in the org that doesn't override them.

## What's here

| File | Used as |
|---|---|
| `profile/README.md` | The org / profile landing page at github.com/smigolsmigol |
| `SECURITY.md` | Default disclosure policy across all repos |
| `CODE_OF_CONDUCT.md` | Contributor Covenant 2.1 default |
| `CONTRIBUTING.md` | Default contribution flow + voice/style rules |
| `SUPPORT.md` | Where to ask for help |
| `CITATION.cff` | Academic citation template |
| `.github/FUNDING.yml` | Sponsorship channels |
| `.github/ISSUE_TEMPLATE/` | Bug / feature / security templates + config |
| `.github/PULL_REQUEST_TEMPLATE.md` | Default PR template |

## Override semantics

Any consumer repo can ship its own copy of any of these files; the per-repo file overrides the org-level default. Use the override sparingly - the point of this repo is uniform baseline.

## Future additions (planned)

- `.github/workflows/security-rust-py.yml` - reusable security workflow for Rust+PyO3 repos
- `.github/workflows/security-python.yml` - reusable security workflow for pure-Python repos
- `.github/workflows/security-typescript.yml` - reusable security workflow for TS repos
- `.github/workflows/scorecard.yml` - reusable OpenSSF Scorecard workflow
- `.github/workflows/release-please.yml` - reusable release automation
- `configs/pre-commit-{rust-py,python,typescript}.yaml` - shared pre-commit hooks

These land in Phase 2 of the chad-foundation rollout. Each consumer repo's local workflow becomes a 5-line `uses:` shim pointing at the reusable here.

## License

MIT.
