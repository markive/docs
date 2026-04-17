# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## About this project

Mintlify documentation site. Pages are MDX files with YAML frontmatter; site configuration lives in [docs.json](docs.json). Production deploys happen automatically on push to the default branch via the Mintlify GitHub app — there is no build step in this repo.

## Common commands

- `mint dev` — local preview at `http://localhost:3000` (run from repo root where `docs.json` lives)
- `mint dev --port 3333` — custom port
- `mint broken-links` — validate internal links before committing
- `mint update` — update the CLI if preview diverges from production
- `npm i -g mint` — install the CLI (requires Node 19+)

## Architecture

- **Navigation is declarative**: Pages only appear in the site if they are listed under `navigation.tabs[].groups[].pages` in [docs.json](docs.json). Adding an `.mdx` file to the repo is not enough — it must be registered there. Paths in `pages` are relative to the repo root and omit the `.mdx` extension.
- **Content layout**: top-level `.mdx` files ([index.mdx](index.mdx), [quickstart.mdx](quickstart.mdx), [development.mdx](development.mdx)) plus topic directories [essentials/](essentials/), [ai-tools/](ai-tools/), [api-reference/](api-reference/). Shared MDX fragments live in [snippets/](snippets/) and are imported into pages.
- **API reference**: driven by [api-reference/openapi.json](api-reference/openapi.json) combined with MDX pages under [api-reference/endpoint/](api-reference/endpoint/).
- **Ignored paths**: [.mintignore](.mintignore) excludes `drafts/` and `*.draft.mdx` from the build (in addition to Mintlify's built-in ignores like `.git`, `node_modules`, `README.md`, `CONTRIBUTING.md`).

## Style (from [AGENTS.md](AGENTS.md) / [CONTRIBUTING.md](CONTRIBUTING.md))

- Active voice, second person ("you"); one idea per sentence.
- Sentence case for headings.
- Bold for UI elements (`**Settings**`); code formatting for file names, commands, paths.

## Mintlify product knowledge

For component reference and writing standards beyond what's here, install the Mintlify skill: `npx skills add https://mintlify.com/docs`.
