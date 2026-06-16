# nixpkg-terrarium

Nix packaging for `@os-eco/terrarium-cli` using Bun and `bun2nix`.

## Package

- Upstream source: `RogerNavelsaker/terrarium`
- Upstream package: `@os-eco/terrarium-cli`
- Pinned version: `0.1.0`
- Installed binary: `terrarium`
- Shortform output: `tl`

## What This Repo Does

- Pins the Terrarium source repo through Nix
- Keeps `bun.nix` in sync with the pinned source repo `bun.lock`
- Builds the upstream CLI as a Bun application with `bun2nix`
- Exposes the canonical binary name `terrarium`

## Files

- `flake.nix`: flake entrypoint
- `nix/package.nix`: Nix derivation
- `nix/package-manifest.json`: pinned source metadata and binary naming
- `bun.lock`: copied from the pinned Terrarium source repo for dependency generation
- `bun.nix`: generated Bun dependency graph used by Nix
- `.github/workflows/sync-github-release.yml`: enabled GitHub-release sync workflow
- `.github/workflows/sync-github-source.yml`: manual GitHub-source sync workflow
- `.github/workflows/sync-npm.yml`: disabled npm-source sync workflow placeholder

## Notes

- The default `out` output installs `terrarium`.
- The shortform `tl` is available as a separate Nix output.
- This repo is packaging-only. Terrarium specs and workflows belong in consumer repos.
- Source of truth is the live GitHub repo today. Keep syncing from `RogerNavelsaker/terrarium` until Terrarium is actually released on npm under `@os-eco` by `jayminwest`.
- `bun run sync:github-release` is the active lane and follows the latest Terrarium Git tag.
- `bun run sync:github-source` is the manual fallback lane for branch-head sync.
- `bun run sync:npm-source` exists only as a disabled handoff point for the future npm-based source path.
