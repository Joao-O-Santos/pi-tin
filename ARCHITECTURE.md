# Architecture

`pi-tin` is a repository scaffold. Projects copy its infrastructure and
own their runtime code independently.

## Runtime skeleton

`src/index.ts` is a deliberately empty Pi extension entry point. A
copied project replaces it with the smallest implementation its tool
needs.

`test/extension.test.ts` provides one smoke test proving that the
package entry point loads. Projects add behavior tests beside it.

## Tooling

Biome formats and lints JavaScript and TypeScript. Code uses tabs and a
100-character formatter ceiling. Pandoc formats tracked Markdown to a
72-character text width.

Dependencies deliberately follow current upstream releases.
`package-lock.json` is disabled so verification exercises the current
dependency graph.

## Documentation

GNU Make assembles the root Markdown documents into `public/` using
Pandoc and small HTML fragments under `templates/`. Static resources
live under `static/`. The arrangement follows the make-it-stop approach
while keeping the template specific implementation small.

The site publishes the same generated `public/` directory on both GitLab
Pages and GitHub Pages.

## CI and release boundary

GitLab CI is authoritative. It verifies every pipeline, publishes GitLab
Pages from `main`, and may publish npm packages from version tags when
the copied package is not private.

GitHub Actions verify pushes and merge requests and publish the mirrored
GitHub Pages site from `main`. GitHub has no release or npm-publishing
workflow.

## Durable state

`PROJECT.md` records accepted scope and direction. `ARCHITECTURE.md`
describes implemented structure. `STYLE.md` records human-readable
conventions. `AGENTS.md` tells coding agents how to work. `SYNC.json`
records which durable artifacts were last acknowledged as current.
