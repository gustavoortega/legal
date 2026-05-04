# Legal

[![License: CC0-1.0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg)](https://creativecommons.org/publicdomain/zero/1.0/)
[![GitHub Pages](https://img.shields.io/badge/GitHub_Pages-live-brightgreen)](https://gustavoortega.github.io/legal/)
[![Privacy First](https://img.shields.io/badge/Privacy-First-green)](#)
[![Signed Commits](https://img.shields.io/badge/Commits-Signed-blue)](https://docs.github.com/en/authentication/managing-commit-signature-verification)

> Public legal documents for my apps — privacy policies, security disclosure paths, and terms.
> Versioned, auditable, and licensed under CC0.

🌐 **Live site:** [gustavoortega.github.io/legal](https://gustavoortega.github.io/legal/)

---

## Why this exists

Every app I publish requires a publicly-accessible, versioned privacy policy. Hosting them in a single Git repository gives:

- **Transparency** — every change is a commit, visible to anyone
- **Auditability** — full history via `git log`, no silent edits
- **Authenticity** — all commits are SSH-signed (`Verified` badge on GitHub)
- **Zero infrastructure** — served by GitHub Pages, free and reliable
- **Reproducibility** — anyone can fork and host their own legal stack the same way

## Apps covered

| App | Platform | Privacy Policy | Status |
|---|---|---|---|
| **PiHelm** | iOS | [pihelm/](https://gustavoortega.github.io/legal/pihelm/) | Active |

## Structure

```
legal/
├── README.md           ← this file
├── LICENSE             ← CC0 1.0 (text released to public domain)
├── SECURITY.md         ← how to report vulnerabilities
├── 404.html            ← custom 404 (no framework leakage)
├── _config.yml         ← Jekyll / GitHub Pages config
├── index.md            ← landing page, lists all apps
└── <app-name>/
    ├── index.md        ← the policy itself (this is the public URL)
    └── CHANGELOG.md    ← human-readable history of material changes
```

Each app has its own folder. The folder name is the URL slug.

## URL conventions

| Document | URL |
|---|---|
| Landing | `https://gustavoortega.github.io/legal/` |
| App policy | `https://gustavoortega.github.io/legal/<app>/` |
| App changelog | `https://gustavoortega.github.io/legal/<app>/CHANGELOG.html` |

App Store Connect receives the **app policy URL** as the Privacy Policy URL.

## Versioning

Every privacy policy includes:

- **Effective date** — when the version became binding for users
- **Last updated** — when the document file was last touched
- **Version** — semver (`MAJOR.MINOR.PATCH`)
  - `MAJOR`: material changes (new data collected, sharing with third parties, etc.) — requires user notification
  - `MINOR`: new sections, clarifications without changing data flows
  - `PATCH`: typos, formatting, link fixes

Old versions are kept as commits in the git history. Use `git log <app>/index.md` to read the full audit trail.

## Adding a new app

1. Create the folder: `mkdir <app-name>`
2. Add `<app-name>/index.md` (the privacy policy — copy from an existing app as template)
3. Add `<app-name>/CHANGELOG.md` starting at `1.0.0`
4. Add the new row to the **Apps covered** table above
5. Add the link in [`index.md`](./index.md)
6. Commit (signed) and push:
   ```bash
   git add .
   git commit -m "feat(<app-name>): add v1.0.0 privacy policy"
   git push
   ```

GitHub Pages rebuilds automatically within ~1 minute.

## Updating an existing policy

1. Edit `<app-name>/index.md` directly
2. Bump the **Version** and **Last updated** fields at the top
3. Add an entry to `<app-name>/CHANGELOG.md` describing what and why
4. If the change is **material** (new data collected, new sharing, etc.):
   - Bump the **Effective date** to a future date (gives users time to review before it applies)
   - Notify existing users in-app
5. Commit (signed) and push

## Security

- See [`SECURITY.md`](./SECURITY.md) for vulnerability disclosure
- All commits are SSH-signed; verify with `git log --show-signature`
- The `main` branch is protected: PRs required, signed commits enforced
- 2FA enabled on the GitHub account

## License

Text content is released under [CC0 1.0 Universal](./LICENSE) (public domain). You are free to copy, modify, and republish without attribution. The structure of this repository is intentionally easy to fork — feel free to do so for your own apps.

## Contact

| Purpose | Channel |
|---|---|
| Privacy questions about a specific app | See the app's privacy policy for app-specific contact |
| Security disclosures | [SECURITY.md](./SECURITY.md) |
| Repository issues (typos, dead links) | [Open an issue](https://github.com/gustavoortega/legal/issues) |
