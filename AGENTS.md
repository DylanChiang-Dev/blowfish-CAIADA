# 中華AI應用發展協會官方網站 Agent Notes

## Start Here

- Read this file first, then `RULES.md`, then the top policy section and latest entries in `MEMORY.md`.
- Keep `README.md` as the human-facing project overview; do not turn it into an agent log.
- Use `MEMORY.md` for durable collaboration notes, decisions, deployment facts, and gotchas.
- Do not write secrets, tokens, private keys, or `.env` values into repository files or logs.

## Repository

- Owner: `DylanChiang-Dev`
- Repository: `blowfish-CAIADA`
- Origin: `https://github.com/DylanChiang-Dev/blowfish-CAIADA`
- Local path: `/Users/dc/Documents/github/DylanChiang-Dev/blowfish-CAIADA`
- Main branch: `main`
- Private: `False`

## Tech Stack

- Hugo static site using the Blowfish theme.
- Blowfish is vendored as ordinary tracked source at `themes/blowfish`.
- The repository root is the Hugo site root; `exampleSite/` is no longer used.

## Common Commands

- Develop: `hugo server`
- Build: `hugo --minify --gc`
- Cloudflare Pages: build command `hugo --minify --gc`, output directory `public`, root directory `/`, `HUGO_VERSION=0.161.1`.

## Work Rules

- Before editing, inspect the relevant source files and existing style.
- Keep changes small and reviewable; avoid unrelated refactors.
- Run the fastest relevant check after changes.
- Commit completed work with a clear Chinese commit message unless the user asks otherwise.
- Push only after the local verification for the change has passed.

## Documentation Map

- `README.md`: project overview for humans.
- `AGENTS.md`: current agent entrypoint and operating notes.
- `RULES.md`: stable repository-specific rules.
- `MEMORY.md`: progressive collaboration memory and historical notes.
- `plans/2026-05-22-官网仓库架构重整计划-v0.0.1.md`: repository architecture restructure plan.
