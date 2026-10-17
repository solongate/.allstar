# .allstar

Org-wide [OpenSSF Allstar](https://github.com/ossf/allstar) security policy configuration for the `solongate` org.

Allstar runs on a schedule (and on push to this repo) via `.github/workflows/allstar.yml`, checking opted-in repositories against the policies below and opening issues on violations.

## Opted-in repositories

- `agent-security`
- `psirtmap`

Configured in [`allstar.yaml`](allstar.yaml) (opt-in strategy — only the repos listed there are scanned).

## Policies enabled

| Policy | File | Action |
|---|---|---|
| Branch Protection | [`branch_protection.yaml`](branch_protection.yaml) | issue |
| Binary Artifacts | [`binary_artifacts.yaml`](binary_artifacts.yaml) | issue |
| CODEOWNERS | [`codeowners.yaml`](codeowners.yaml) | issue |
| Outside Collaborators | [`outside.yaml`](outside.yaml) | issue |
| SECURITY.md | [`security.yaml`](security.yaml) | issue |
| Dangerous Workflow | [`dangerous_workflow.yaml`](dangerous_workflow.yaml) | issue |
| Generic Scorecard Check | [`scorecard.yaml`](scorecard.yaml) | issue |
| GitHub Actions | [`actions.yaml`](actions.yaml) | issue |
| Repository Administrators | [`admin.yaml`](admin.yaml) | log (no allow-list configured yet; switch to `issue` after reviewing current admins) |

A repo can override any of these from its own `.allstar/` directory once repo override is allowed for that policy.

## Operating this

Runs as a GitHub Action using the `solongate-allstar` GitHub App (App ID `5358869`). Credentials live in the `prod` environment on this repo:

- `APP_ID` (environment variable) — `5358869`
- `PRIVATE_KEY` (environment secret) — the App's private key

See [ossf/allstar's operator docs](https://github.com/ossf/allstar/blob/main/operator.md) for policy semantics and [github-action-installation.md](https://github.com/ossf/allstar/blob/main/github-action-installation.md) for the Action runner itself.