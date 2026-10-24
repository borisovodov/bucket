# Scoop Bucket for Dóru

[![Tests](https://github.com/borisovodov/bucket/actions/workflows/ci.yml/badge.svg)](https://github.com/borisovodov/bucket/actions/workflows/ci.yml)

Scoop bucket for [Dóru](https://doru.family) — local-first genealogy for the
AI era.

## Install

```pwsh
scoop bucket add bucket https://github.com/borisovodov/bucket
scoop install doru
```

The manifest installs the Windows NSIS build from the project's GitHub
releases by extracting it as a 7z archive (Scoop's portable install path):
the app is unpacked into the scoop app directory without running the NSIS
installer, so no registry keys or file associations are created — open
`.doru` files from inside the app. The app's own data lives in
`%APPDATA%\Doru`, outside the scoop directory.

## Updating manifests

`checkver`/`autoupdate` in each manifest track the GitHub releases of the
corresponding project:

```pwsh
.\bin\checkver.ps1 -u      # list outdated manifests and download new hashes
```

The `ci.yml` workflow runs the bucket's Pester test suite on every push to
validate manifests (schema, URLs, hashes, checkver).

## Repository settings

The `ci.yml` workflow requires GitHub Actions to be enabled with
**Allow all actions and reusable workflows** (repository Settings → Actions
→ General).
