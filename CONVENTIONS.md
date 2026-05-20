# Conventions

This document defines the naming conventions, structure, and standards for all
workflows in this repository.

## Language

All code, documentation, comments, commit messages, branch names, and PR
descriptions **must be written in English**.

## Branch Naming

All branches created in this repository (and recommended for caller repositories) must follow a structured naming convention using category prefixes. This ensures logical grouping and clarity:

- `feature/` — New features, additions, or enhancements (e.g., `feature/add-ansible-publish`)
- `bugfix/` — Fixing a bug or unexpected behavior (e.g., `bugfix/fix-trufflehog-version`)
- `hotfix/` — Critical fixes deployed directly to production (e.g., `hotfix/security-patch`)
- `release/` — Release branches (e.g., `release/v0.4.0`)
- `docs/` — Documentation updates (e.g., `docs/update-readme`)
- `refactor/` — Code changes that neither fix a bug nor add a feature (e.g., `refactor/cleanup-matrix`)
- `test/` — Adding missing tests or correcting existing tests (e.g., `test/add-molecule-case`)
- `chore/` — Maintenance, updating build files or dependencies (e.g., `chore/bump-python-version`)
- `ci/` — Pipeline, rules, or CI/CD specific changes (e.g., `ci/harden-actionlint`)

Branch names are validated automatically on every Pull Request. Invalid branch names will fail the `Branch Name Lint` job and block the PR merge.

## File Naming

Reusable workflows follow the schema:

```text
{technology}-{action}.yml
```

| Prefix       | Technology                | Example Files                                                              | Status     |
| ------------ | ------------------------- | -------------------------------------------------------------------------- | ---------- |
| `ansible-`   | Ansible roles/collections | `ansible-ci.yml`, `ansible-publish-galaxy.yml`                             | ✅ Active  |
| `terraform-` | Terraform / OpenTofu      | `terraform-validate.yml`, `terraform-plan.yml`, `terraform-apply.yml`      | 📋 Planned |
| `aca-`       | Azure Container Apps      | `aca-build.yml`, `aca-deploy.yml`                                          | 📋 Planned |
| `docker-`    | Docker images             | `docker-build-push.yml`, `docker-security-scan.yml`                        | 📋 Planned |
| `shared-`    | Cross-cutting / universal | `shared-security-scan.yml`, `shared-release-please.yml`                    | 📋 Planned |

### Reserved Names

- `ci.yml` — CI pipeline for this repository itself (not a reusable workflow).
  This is the enterprise standard naming convention used by GitHub, Kubernetes,
  HashiCorp, and Red Hat for the primary validation pipeline.

## Job Naming

Job IDs use **kebab-case**. Display names use **plain text** — no emoji, no
numbering. This follows the enterprise convention observed in GitHub starter
workflows, HashiCorp Terraform, Red Hat Ansible, and Kubernetes.

```yaml
jobs:
  yaml-lint:
    name: "YAML Lint"

  ansible-lint:
    name: "Ansible Lint"

  molecule-test:
    name: "Molecule — ${{ matrix.scenario }} / ${{ matrix.distro }}"

  security-scan:
    name: "Security Scan"

  publish-galaxy:
    name: "Publish to Galaxy"

  merge-check:
    name: "Merge Check"
```

| Rule                     | Example                                        | Purpose                              |
| ------------------------ | ---------------------------------------------- | ------------------------------------ |
| Kebab-case ID            | `yaml-lint`, `molecule-test`                   | Consistency, no spaces               |
| Plain text `name:`       | `"YAML Lint"`                                  | Enterprise standard, no emoji        |
| Matrix in `name:`        | `"Molecule — default / ubuntu2404"`            | Shows what is being tested           |
| Gate job = `merge-check` | `name: "Merge Check"`                          | Unified gate across all repositories |

## Step Naming

Step names start with a **verb** describing the action. No numbering, no emoji.

```yaml
steps:
  - name: "Checkout repository"
  - name: "Install dependencies"
  - name: "Run Molecule test"
  - name: "Upload to Ansible Galaxy"
```

| Rule              | ✅ Correct              | ❌ Incorrect                |
| ----------------- | ---------------------- | -------------------------- |
| Start with a verb | `Install dependencies` | `Dependencies installation`|
| No numbering      | `Checkout repository`  | `1.1 Checkout Code`        |
| No emoji          | `Run Molecule test`    | `🧪 Run Molecule test`     |

## Repository Structure

```text
.github/workflows/
├── ci.yml                         # CI for this repo (yamllint + actionlint)
├── ansible-ci.yml                 # Reusable: Ansible lint + molecule
├── ansible-publish-galaxy.yml     # Reusable: publish to Galaxy
├── terraform-validate.yml         # [Planned]
├── terraform-plan.yml             # [Planned]
└── ...                            # Future technologies
```

## Merge Check Pattern

Every reusable CI workflow includes a `merge-check` job that aggregates results
from all other jobs into a **single status check**. This is the only check
required in branch protection rules.

Benefits:

- No need to update branch protection when jobs are added or removed
- Matrix jobs with dynamic names are covered automatically
- All validation jobs are **hard requirements** — use inline suppression
  comments (e.g., `#noinspection`, `# actionlint-ignore`) for known false
  positives instead of `continue-on-error`

```yaml
merge-check:
  name: "Merge Check"
  needs: [job-a, job-b, job-c]
  if: always()
  runs-on: ubuntu-latest
  steps:
    - name: "Evaluate results"
      run: |
        # Check hard-requirement jobs here
        if [[ "${{ needs.job-a.result }}" != "success" ]]; then
          echo "::error::Job A failed"
          exit 1
        fi
        echo "All validations passed"
```

## Security Practices

This repository follows [GitHub's security hardening guidelines](https://docs.github.com/en/actions/security-for-github-actions/security-guides/security-hardening-for-github-actions):

- **Least-privilege permissions** — All workflows declare `permissions:` at the
  top level with the minimum required scope (typically `contents: read`).
- **Pin actions to version tags** — Third-party actions are pinned to a specific
  major version tag (e.g., `@v6`). Full SHA pinning is recommended for
  production caller workflows.
- **No inline secrets** — Secrets are never hardcoded; they are passed via
  `secrets:` in `workflow_call`.
- **Concurrency control** — Workflows use `concurrency` groups to cancel stale
  runs and prevent resource waste.
- **CODEOWNERS** — All workflow files require review from designated owners
  before merging.
