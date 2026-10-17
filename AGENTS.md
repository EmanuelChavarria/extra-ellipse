# AGENTS.md

## What this repo is

`extra-ellipse` is a stock **Astro 7.4.0 "basics" starter**: one package (`astro`), a
single static page, no adapter, and no integrations. There is **no React/Vue/Svelte,
no Tailwind, no content collections, no i18n, and no test/lint/format setup** — do not
assume any of these exist; add them deliberately if needed.

- Package manager is **Bun** (`bun.lock` is the only lockfile — do not add an
  npm/pnpm/yarn lockfile).
- Node engine is declared `>=22.22.0` in `package.json`.

## Commands

```sh
bun install        # install dependencies
bun run dev        # dev server (see "Dev server" below)
bun run build      # static output to ./dist/
bun run preview    # serve the built output
```

There is **no `test`, `lint`, or `format` script**, and `astro check` is **not usable out
of the box**: typechecking requires `@astrojs/check` + `typescript`, neither of which is
installed. Do not invent those commands; install the tooling first if you need it.

## Dev server: background mode is required for agents on Windows

Astro 7 detects agentic environments (via `am-i-vibing`) and, on non-Windows platforms,
auto-starts `astro dev` as a background process. **That auto-backgrounding is disabled on
Windows**, where detached children are killed with the agent's job object — so an agent on
Windows must pass the flag explicitly:

```sh
bun run astro dev --background      # start a tracked background dev server
bun run astro dev status            # is one running?
bun run astro dev logs [--follow]   # read its logs (optionally follow)
bun run astro dev stop              # stop it
```

Gotchas:

- Background servers are found through a **lock file**, so `stop`/`status`/`logs` only
  work for servers started with `--background`.
- `--background` cannot be combined with `--ignore-lock`, and `--force` cannot be
  combined with `--ignore-lock`.
- A foreground `astro dev` refuses to start while another server is already running
  unless you pass `--force` (replace it) or `--ignore-lock` (run alongside it, untracked).
- When Astro detects an agent it also forces `--json` output from `astro dev`.

## Generated files

`.astro/` and `dist/` are generated and gitignored. `.astro/types.d.ts` (referenced by
`tsconfig.json`) does not exist until `astro dev`, `astro build`, or `astro sync` runs — so
run one of those before relying on generated types.

`tsconfig.json` extends `astro/tsconfigs/strict`.

## Repo state

Public GitHub repo `https://github.com/EmanuelChavarria/extra-ellipse`, default branch `master`.
**No CI**: there are no workflows, and no `test`/`lint`/`format` scripts.

## Deploy

Production is the Vercel project `extra-ellipse` (team `por-wore`), live at
https://extra-ellipse.vercel.app. The build runs on Vercel with Bun and the detected Astro
preset. Deploy with `vercel deploy --prod --yes` from this directory.

## Docs

https://docs.astro.build
