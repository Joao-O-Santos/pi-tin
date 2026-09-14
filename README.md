# pi-tin

<p align="center">
  <img src="https://gitlab.com/Joao-O-Santos/pi-tin/-/raw/main/logo.png" alt="pi-tin logo" width="240">
</p>

[![pipeline
status](https://gitlab.com/Joao-O-Santos/pi-tin/badges/main/pipeline.svg)](https://gitlab.com/Joao-O-Santos/pi-tin/-/commits/main)
[![license](https://img.shields.io/gitlab/license/Joao-O-Santos%2Fpi-tin)](https://gitlab.com/Joao-O-Santos/pi-tin/-/commits/main)


A small reusable mould for J's Pi Bakery projects.

`pi-tin` is a repository template, not a runtime dependency. It keeps
the boring parts of small Pi extensions consistent: package metadata,
formatting, verification, documentation, GitLab publishing, and mirrored
Pages builds.

The template deliberately tracks current upstream tooling. It does not
pin dependency versions or commit a package lock. If upstream changes
break a project, update the project rather than preserving old tool
behavior.

## Use

Duplicate this repository for a new project, then:

1.  Rename the project and package metadata.
2.  Replace the placeholder extension in `src/index.ts`.
3.  Update `PROJECT.md`, `ARCHITECTURE.md`, `STYLE.md`, and `SYNC.json`.
4.  Add the smallest tests needed for the package.
5.  Run `make verify` and `make site`.
6.  Remove `"private": true` only if the package should publish to npm.

GitLab is canonical and the only release authority. GitHub may mirror
the repository, run verification, and publish GitHub Pages, but it must
not publish releases or npm packages.

## Included conventions

-   TypeScript with strict checking.
-   Biome with tabs and a 100-character formatter ceiling.
-   Markdown hard-wrapped to 72 columns with Pandoc.
-   Commit subjects use an imperative capitalized verb and stay within
    50 characters.
-   No conventional-commit prefixes such as `fix:` or `chore:`.
-   No dependency or action pinning; projects follow current upstream.
-   No committed `package-lock.json`.
-   A small make-it-stop-style documentation site.
-   GitLab CI for verification, Pages, and optional npm publishing.
-   GitHub Actions for verification and Pages only.
-   CI installs the current Pandoc release automatically.

## Project files

`PROJECT.md` describes accepted scope and direction. `SYNC.json` records
which durable artifacts are current. `ARCHITECTURE.md` describes the
implemented structure. `STYLE.md` records human-readable conventions.
`AGENTS.md` gives coding agents operational constraints. `CHANGELOG.md`
records user-visible changes.

## Development

```sh
npm install
make verify
make site
```

Pandoc must be available on `PATH` for local verification and site
builds.
The CI workflows install the current release with
`scripts/install-latest-pandoc.mjs`; local development should install
Pandoc through the operating system's package manager.

The generated site is written to `public/` and is ignored by Git.
