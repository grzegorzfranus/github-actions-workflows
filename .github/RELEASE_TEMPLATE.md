# Release Template

This template defines the standard structure for all GitHub Releases in this project.
When drafting a new release, copy the contents of this template, fill in the placeholders, and use it as the release description.

---

# v[X.Y.Z]
Release v[X.Y.Z] — [One-line summary of the main feature/theme]

**Date:** [YYYY-MM-DD]  
**Scope:** [Affected component/technology/role, e.g., ansible-role-tailscale]  
**Release type:** [Major / Minor / Patch] ([brief reason, e.g., new platform support, bug fixes])  

## 🧭 Summary
[Provide a brief 1-2 paragraph description of the release, the motivation behind it, any major architectural changes, and key highlights.]

## 🌟 Highlights
- **[Feature Name]** — [Key detail about the feature and why it matters.]
- **[Feature Name]** — [Key detail about the feature and why it matters.]

## ✨ Added
- [New feature, input, or variable added]
- [New file or component introduced]
- [New test scenario or platform added to CI/CD]

## 🐛 Fixed
- [Description of the bug, root cause, and how it was fixed]

## 🔄 Changed
- [Details of internal changes, refactorings, or updates to dependencies]

## ⚠️ Behavior changes and migration
- [Describe any breaking changes, deprecations, or updates that require user action]
- [If there are no behavior changes, state: "None. Existing deployments are unaffected."]

## 🔗 Compatibility
| Platform / Tool | Versions |
| --------------- | -------- |
| [e.g. Ansible]  | [e.g. >= 2.16] |
| [e.g. Ubuntu]   | [e.g. 24.04] |
| [e.g. Python]   | [e.g. >= 3.9] |

## 🧪 Validation checklist
- [ ] **yamllint**: [e.g., clean — 0 errors]
- [ ] **ansible-lint**: [e.g., clean — 0 failures]
- [ ] **Molecule / Tests**: [e.g., Passed on Ubuntu 24.04, Rocky Linux 9]

## ℹ️ Known issues
- [Description of any known issues or limitations in this release. State "None" if there are none.]

## 📚 References
- **CHANGELOG:** [Link to CHANGELOG.md entry]
- **README:** [Link to README.md]
- **Documentation / Links:** [Any external links or documentation]
