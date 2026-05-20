# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.2.0] - 2026-05-20

### Added

- `ansible-ci.yml` — Reusable workflow for Ansible CI (YAML lint, Ansible lint, TruffleHog security scan, Molecule tests, merge check gate)
- `ansible-publish-galaxy.yml` — Reusable workflow for publishing roles to Ansible Galaxy with pre-publish linting, validation, and retry logic

## [0.1.0] - 2026-05-20

### Added

- Repository initial setup with Apache-2.0 license
- `ci.yml` — CI pipeline with YAML lint, Actions lint (hard gate), and merge
  check gate
- `CONVENTIONS.md` — Naming conventions for files, jobs, steps, and security
  practices
- `CHANGELOG.md` — Keep a Changelog format with Semantic Versioning
- `README.md` — Project documentation with usage examples and input reference
- `CODEOWNERS` — Auto-assign PR reviews
- `.yamllint` — YAML lint configuration for GitHub Actions files
- `.gitignore` — Standard ignores for OS, editor, and Python artifacts
