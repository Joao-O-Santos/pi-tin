# Project

## Objective

Maintain `pi-tin` as a small reusable template for J's Pi Bakery
projects.

## Intended use

Use the repository as the starting shape for small Pi extensions and
companion tools. The template should remove repetitive setup without
becoming a shared runtime framework.

## Scope

The template provides package metadata, TypeScript and Biome
configuration, basic tests, durable project files, Markdown formatting,
a make-it-stop-style documentation build, GitLab CI, and GitHub
verification and Pages workflows.

## Constraints

Keep the template small and understandable in one sitting. Prefer
platform and Node.js primitives over wrappers. Track current upstream
releases rather than pinning tool versions. GitLab is canonical and is
the only release authority.

## Definition of done

A copied project can replace the placeholder extension, edit its
identity and documentation, run `make verify`, build the same site on
GitLab and GitHub Pages, and opt into npm publishing from GitLab without
inheriting unnecessary runtime abstractions.

## Current direction

Keep infrastructure reusable through copying, not through a common
runtime package. Add shared runtime code only after several projects
independently need the same behavior and a standard-library primitive is
insufficient.
