# esams-hq/.github

Organization-wide defaults for **eSAMS** (Electronic School Administration & Management System).

| Path | Purpose |
|---|---|
| `profile/README.md` | Public organization profile shown on github.com/esams-hq |
| `CONTRIBUTING.md`, `SECURITY.md`, `CODE_OF_CONDUCT.md`, `SUPPORT.md` | Default community health files for every repo without its own |
| `.github/ISSUE_TEMPLATE/` | Default issue forms (bug, feature) |
| `.github/pull_request_template.md` | Default PR checklist |
| `.github/workflows/` | **Reusable workflows** called by other repos (Laravel CI, Next.js CI, Azure deploy) |
| `workflow-templates/` | Starter workflows shown under *Actions → New workflow* in every org repo |

## Setup

1. Create the repository `esams-hq/.github` and make it **public** (required for default community health files and org profile). Keep secrets and internal details out of it.
2. Push these files to `main`.
3. Org settings → Actions → General: allow actions from `esams-hq` and GitHub-verified creators.
4. For each deployable repo (e.g. `api`), create environments `staging` and `production` (add required reviewers on `production`).
5. Add these **secrets** at org level (Azure OIDC federated credential, no passwords):
   - `AZURE_CLIENT_ID`
   - `AZURE_TENANT_ID`
   - `AZURE_SUBSCRIPTION_ID`
6. In each repo, add `.github/dependabot.yml` (Dependabot config cannot be set org-wide).

## Using the reusable workflows

```yaml
jobs:
  ci:
    uses: esams-hq/.github/.github/workflows/laravel-ci.yml@main
```

Pin to a tag (e.g. `@v1`) once the workflows are stable.
