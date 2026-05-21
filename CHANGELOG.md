# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.7.0](https://github.com/grzegorzfranus/github-actions-workflows/compare/v0.6.4...v0.7.0) (2026-05-21)


### Features

* add Galaxy description length validation to pre-publish ([#17](https://github.com/grzegorzfranus/github-actions-workflows/issues/17)) ([1819177](https://github.com/grzegorzfranus/github-actions-workflows/commit/18191778c1955a7eca45fc72ba98af01291bf542))

## [0.6.4](https://github.com/grzegorzfranus/github-actions-workflows/compare/v0.6.3...v0.6.4) (2026-05-20)


### Code Refactoring

* simplify pre-publish validation in ansible-publish-galaxy ([#15](https://github.com/grzegorzfranus/github-actions-workflows/issues/15)) ([b29da30](https://github.com/grzegorzfranus/github-actions-workflows/commit/b29da309aaee4cf6e64848dd798109c5a8b4cf90))

## [0.6.3](https://github.com/grzegorzfranus/github-actions-workflows/compare/v0.6.2...v0.6.3) (2026-05-20)


### Code Refactoring

* rename internal merge-check to CI Gate ([#12](https://github.com/grzegorzfranus/github-actions-workflows/issues/12)) ([6ece884](https://github.com/grzegorzfranus/github-actions-workflows/commit/6ece884f28898edbc4c6aac6e2949e5d77d91017))


### Miscellaneous

* add changelog-sections to Release Please config ([#13](https://github.com/grzegorzfranus/github-actions-workflows/issues/13)) ([25ed987](https://github.com/grzegorzfranus/github-actions-workflows/commit/25ed987994e35d727db3b4191a10774bbbae2ba6))

## [0.6.2](https://github.com/grzegorzfranus/github-actions-workflows/compare/v0.6.1...v0.6.2) (2026-05-20)


### Bug Fixes

* add --repo flag to gh CLI in release validation ([baf5ab6](https://github.com/grzegorzfranus/github-actions-workflows/commit/baf5ab6329b135983386d5c11c2e3be71cd1ec39))
* add --repo flag to gh CLI in release validation ([44526ad](https://github.com/grzegorzfranus/github-actions-workflows/commit/44526ad3881f29db6b635dc2dee0d77bfbe414cb))
* enforce job ordering and upgrade actions/cache to v5 ([e2decc9](https://github.com/grzegorzfranus/github-actions-workflows/commit/e2decc985634b6654fbc140d85139bd25a17ce65))
* enforce job ordering and upgrade actions/cache to v5 ([43c5acd](https://github.com/grzegorzfranus/github-actions-workflows/commit/43c5acd0bcc85cea9db6574ec92cddbdb718c834))

## [0.6.1](https://github.com/grzegorzfranus/github-actions-workflows/compare/v0.6.0...v0.6.1) (2026-05-20)


### Bug Fixes

* add inline CI validation for Release Please PRs ([9eb072d](https://github.com/grzegorzfranus/github-actions-workflows/commit/9eb072d98cad86d5ba71c8d52237f72cbbe292dc))

## [0.6.0](https://github.com/grzegorzfranus/github-actions-workflows/compare/v0.5.0...v0.6.0) (2026-05-20)


### Features

* add ansible-ci.yml reusable workflow ([8f8b945](https://github.com/grzegorzfranus/github-actions-workflows/commit/8f8b94587b8189ada4738913ffbcb88762a0b89e))
* add ansible-publish-galaxy.yml workflow ([a71fd4b](https://github.com/grzegorzfranus/github-actions-workflows/commit/a71fd4b969e5ead60cbd507ec8f204020b80ca8e))
* add automated versioning with Google Release Please ([ec22af8](https://github.com/grzegorzfranus/github-actions-workflows/commit/ec22af857d045a8aedae845a369d0a3cb7a75fb2))
* add automated versioning with Google Release Please ([14e5937](https://github.com/grzegorzfranus/github-actions-workflows/commit/14e59377e137356a7b8b5685682182cbeb48e844))
* add RELEASE_TEMPLATE.md for release notes ([68544dd](https://github.com/grzegorzfranus/github-actions-workflows/commit/68544ddd30b3a1274347e630b992994ffa88f119))
* add RELEASE_TEMPLATE.md for release notes ([2505e82](https://github.com/grzegorzfranus/github-actions-workflows/commit/2505e82edbda4ce7b3addc12da9580e03ca872d4))
* implement branch name linter as a CI pre-hook ([dc1a96f](https://github.com/grzegorzfranus/github-actions-workflows/commit/dc1a96f0589b69a7d7ac5d6e378a355f70469038))
* implement branch name linter as a CI pre-hook ([bcd80c9](https://github.com/grzegorzfranus/github-actions-workflows/commit/bcd80c9ca203954234d943891cb0a15af831141e))
* initial repository setup with CI, conventions, and documentation ([9a96143](https://github.com/grzegorzfranus/github-actions-workflows/commit/9a96143fb04ac28ec5b2013268bdf8a6b6e4d6c3))
* initial repository setup with CI, conventions, and documentation ([e303732](https://github.com/grzegorzfranus/github-actions-workflows/commit/e303732886ca99b0ed6fc081572031aff94811ee))


### Bug Fixes

* change trufflehog action version to main ([f5e0773](https://github.com/grzegorzfranus/github-actions-workflows/commit/f5e07738465c8e7c30dd93d4857c3494dac4f22c))
* make actionlint a hard requirement in merge check gate ([3c8f9fb](https://github.com/grzegorzfranus/github-actions-workflows/commit/3c8f9fb83f19df103046540b8b6b45445a601861))

## [0.5.0] - 2026-05-20

### Added

- `release.yml` — Automated versioning and release management via Google Release Please
- `release-please-config.json` — Release Please configuration (simple release type, v-prefixed tags)
- `.release-please-manifest.json` — Version tracker for Release Please
- Conventional Commits convention documented in `CONVENTIONS.md`
- Versioning and Releases section added to `CONVENTIONS.md`

### Changed

- `ci.yml` — Branch name regex updated to allow `release-please--` auto-generated branches

## [0.4.0] - 2026-05-20

### Added

- `ci.yml` — Branch name linting step for PRs with detailed Markdown Job Summary feedback on naming failures

## [0.3.0] - 2026-05-20

### Added

- `RELEASE_TEMPLATE.md` — Standard template for drafting detailed, cross-platform enterprise release notes

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
