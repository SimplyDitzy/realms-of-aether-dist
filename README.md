# Realms of Aether — Distribution

Public distribution channel for the **Realms of Aether** launcher.

This repo holds **no game source code** — only:
- `channels/<channel>.json` — the version manifest the launcher reads (version + the
  download URL, SHA-256 and size of the build).
- **Releases** — the actual build zips, attached as release assets.

The game's source lives in a separate private repo. The launcher fetches
`channels/live.json` from here over plain HTTPS (no auth, because this repo is public)
and downloads the build from the matching Release.

## Publishing a build (manual for now; automated in CI later)

1. In the game repo, run `scripts/build_release.ps1` to produce
   `dist/<version>/RealmsOfAether-windows-<version>.zip` and update the manifest.
2. Create a Release here tagged `v<version>` and upload that zip as an asset.
3. Commit the updated `channels/live.json` here.
