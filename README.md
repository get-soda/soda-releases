# soda-releases

Public distribution channel for the Soda macOS desktop app. Sparkle fetches
`appcast.xml` from this repo and downloads signed artifacts from `releases/`.

## Layout

```
soda-releases/
├── appcast.xml            # Sparkle feed, regenerated on every release
└── releases/
    ├── Soda-1.0.0.zip     # Signed + notarized + stapled app bundle
    ├── Soda-1.1.0.zip
    ├── Soda-1.1.0.delta   # Binary delta from 1.0.0 → 1.1.0 (auto-generated)
    └── Soda-1.1.0.html    # Optional release notes (linked from appcast)
```

## Publishing a release

Releases are published from the main Soda repo via `scripts/release.sh`.
See that script's header for the full workflow.

This repo is append-only from the release script's perspective — do not edit
`appcast.xml` or files in `releases/` by hand. Re-running `release.sh` is the
supported way to fix a bad release.

## Keep old versions

Retain the last ~4 `.zip` files even after deprecation — `generate_appcast`
needs them to produce binary deltas for users on older versions. If a file is
deleted, users on that version fall back to the full download (not a hard
failure, just bigger).

## Do not publish

- EdDSA private key (kept in the release-machine keychain only).
- Unsigned or non-notarized builds.
- Pre-release builds on the stable channel. Add a `-beta` suffix to the version
  to keep Sparkle's channel filtering working if/when a beta channel is added.
