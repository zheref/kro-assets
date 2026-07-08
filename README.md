# kro-assets

Shared, **public** asset host for the **Kro** product across **all its flavors and
target apps** — **KroApple** (iOS / macOS), **KroAndroid**, **Kro** (Web), and any
future platform.

## Why this exists

The product repos are **private**. GitHub does **not** render inline images in a
private repo's PR / issue descriptions when they're referenced via
`raw.githubusercontent.com` — its image proxy (camo) fetches anonymously and
can't authenticate to a private repo, so the image 404s and shows broken.
Screenshot / snapshot images that a PR needs to **show inline** therefore can't
live only in the private repo.

This repo is **public**, so
`https://raw.githubusercontent.com/zheref/kro-assets/<sha>/<path>` is
anonymously fetchable and **renders inline in any repo's markdown** — including
the private product repos' PR descriptions.

## What belongs here

- **PR screenshots** sourced from snapshot / visual-regression tests — the
  recorded test images **are** the screenshots (never separately-staged
  captures).
- Any other **renderable, non-sensitive** asset a private Kro product repo needs
  to embed inline (diagrams, badges, etc.).

> **Public and non-sensitive only.** Everything here is world-readable. Snapshot
> images must be rendered from `#if DEBUG` / mock fixtures — **never** real
> account/session data (data minimization).

## Layout

```
<product-repo>/pr-<number>/<scene>.png
```

e.g. `KroApple/pr-95/votableCounts.png`. Reference the images **pinned to a
commit SHA** for stability:

```
<img src="https://raw.githubusercontent.com/zheref/kro-assets/<sha>/KroApple/pr-95/votableCounts.png" width="240">
```

## Consumers (per-platform "UI screenshots" rule)

- **KroApple** — `.claude/rules/16-ui-screenshots.md`
- **KroAndroid** — its equivalent UI-screenshots rule
- **Kro (Web)** — its equivalent UI-screenshots rule

All of them implement bankai-core handbook **UZF-26** (UI PRs carry snapshot
screenshots); this repo is the shared **hosting** mechanism they use.
