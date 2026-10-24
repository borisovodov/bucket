# Personal Scoop Bucket

[![Tests](https://github.com/borisovodov/bucket/actions/workflows/ci.yml/badge.svg)](https://github.com/borisovodov/bucket/actions/workflows/ci.yml)

A personal [Scoop](https://scoop.sh) bucket for applications I distribute
through Scoop. Install the bucket, then any app from it:

```pwsh
scoop bucket add bucket https://github.com/borisovodov/bucket
scoop install <app>
```

## Apps

| App | Description | Homepage |
|---|---|---|
| [doru](bucket/doru.json) | Local-first genealogy for the AI era | https://doru.family |

Dóru's manifest installs the Windows NSIS build portably: the installer is
extracted as a 7z archive into the scoop app directory, so no registry keys
or file associations are created — open `.doru` files from inside the app.
The app's own data lives in `%APPDATA%\Doru`, outside the scoop directory.

## Updating manifests

Every manifest carries `checkver`/`autoupdate` blocks that track the
upstream GitHub releases:

```pwsh
.\bin\checkver.ps1 -u      # list outdated manifests and download new hashes
```

The `ci.yml` workflow runs the bucket's Pester test suite on every push and
validates all manifests (schema, URLs, hashes, checkver).

## Repository settings

The workflows use third-party actions and need **Read and write** workflow
permissions: repository Settings → Actions → General → *Allow all actions
and reusable workflows*, and *Workflow permissions* → **Read and write
permissions**.
