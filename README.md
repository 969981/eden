# Eden — Forgejo source mirror and automatic desktop builds

This is an **unofficial** source mirror/build automation repository for the [Eden emulator](https://git.eden-emu.dev/eden-emu/eden).

## Branch policy

- `main`: GitHub Actions and this documentation (not the emulator source branch).
- `upstream-master`: exact official Forgejo `master` commit, synchronized every ~10 minutes.
- Releases: one **prerelease** per upstream source commit, only after Windows, Linux and macOS builds all pass.

**Official upstream Git URL:** `https://git.eden-emu.dev/eden-emu/eden.git`  
**Fallback:** `https://github.com/eden-emulator/mirror.git` (official GitHub mirror; may lag).

GitHub scheduled workflows are best-effort, not guaranteed to run exactly on minute 0/10/20/30/40/50.

## Desktop packages

- Windows x64: MinGW + Qt bundled into a portable ZIP.
- Linux x64: Ubuntu 24.04 archive; requires compatible host libraries; **not** an AppImage.
- macOS arm64 (Apple Silicon): experimental ad-hoc-signed DMG, not notarized.

The workflow uses upstream CMake/Qt build recipes adapted from the working workflows in [969981/Eden-NS2](https://github.com/969981/Eden-NS2). Future upstream changes can require maintenance. Failed builds do not produce a release; the next scheduled/manual run retries.

## Usage

Choose **Actions → Sync Eden Forgejo and release → Run workflow** to check/sync manually.
The workflow uses the built-in GitHub Actions token for source branch pushes and release uploads. Repository Actions must allow **Contents: read and write**.

The original developers maintain the canonical source and their own releases. These snapshot builds contain no games, firmware or decryption keys; compilation alone does not demonstrate emulator compatibility.
