# Feature: Coffee-shop landing page (Altura)

Objective: Build a single-page Astro landing site for a specialty coffee shop with a product
catalog, an origin/sourcing section, and a contact/order form, in Spanish.
Branch: `feat/coffee-shop-landing`
Delivery strategy: `single-pr` (one coherent change set / one PR-equivalent branch)
Test runner: none configured — verification is `bun run build` + output inspection.

## Specs

- **S1** — Landing page for a coffee shop, Astro, all user-facing copy in Spanish.
- **S2** — Product catalog section (catálogo) with at least 6 products; each with image,
  name, tasting notes and price.
- **S3** — Origin section (origen) showing sourcing: finca/país, altitud, variedad, proceso.
- **S4** — Contact/order form (formulario de contacto/pedidos) with client-side validation
  and a success state. Static site: no backend, and the UI must say so.
- **S5** — Real Pexels images, downloaded into the repo (self-contained, no hotlinking).
- **S6** — Responsive and accessible: labelled inputs, real `alt` text, visible focus,
  `prefers-reduced-motion` respected.
- **S7** — Deploy to Vercel when done.
- **S8** — Run ODD automatically, persist to engram, deliver as `single-pr`.

## Tasks

- [x] T1 — Project setup: design tokens, fonts, base Layout, global styles. (inline)
- [x] T2 — Nav + Hero. (inline)
- [x] T3 — Catálogo de productos. (inline)
- [x] T4 — Sección Origen. (inline)
- [x] T5 — Contacto / formulario de pedidos. (inline)
- [x] T6 — Footer, scroll-reveal, responsive + a11y pass. (inline)
- [x] T7 — `bun run build` + verify output. (inline)
- [x] T8 — Work-unit commits on feature branch. (inline)
- [x] T9 — Vercel deploy. (inline)

## Log

- **L1** (verbatim, user): "Usando la skill de astro y la skill design-taste-fronted, crea una
  landing-page para una tienda de cafe donde esta cuenta con un catalogo de productos, seccion
  de origen y formulario de contacto/pedidcos. Puedes usar imagenes de pexel. Usa sdd en modo
  automatico + engram y en modo y en delivery-modo single-pr una vez dtermines, depliega en verce"
- **L2**: Target repo = `extra-ellipse` (user choice). Site copy = Spanish (user did not object).
- **L3** (finding): skills `astro` and `design-taste-fronted` are NOT installed on this machine;
  neither is any `sdd` mode. Interpreted as ODD automatic + engram + `single-pr`. Design done
  by hand with a deliberate direction instead. Recorded in engram.
- **L4** (finding): `vercel` CLI not installed and no Vercel auth → S7/T9 blocked pending user
  installing the CLI and logging in.
- **L5**: Design direction — brand "Altura" (café de altura). Warm editorial palette
  (espresso/crema/caramelo), Fraunces display + Inter body, scroll-reveal, sticky nav.
  10 Pexels photos downloaded into `src/assets/` (self-contained) and optimized by Astro.
- **L6**: Verification — `bun run build` green: 1 page, 28 optimized WebP variants. Output
  inspected: all section ids present, 9 `<img>` with `srcset` + real `alt`, no external Pexels
  URLs, no references to the removed starter files. `lang="es"`, `charset="utf-8"`.
- **L7** (deploy): Unblocked — Vercel CLI 64.5.0 installed globally via `bun add -g vercel`; user
  ran `vercel login` (session `chavariae249-4007`). `vercel deploy --prod --yes` created project
  `por-wore/extra-ellipse` and built on Vercel (Astro detected, `bun.lock` → Bun, `bun run build`).
  Result `readyState: READY`.
  - Production alias: https://extra-ellipse.vercel.app
  - Deployment URL: https://extra-ellipse-b79pet2zx-por-wore.vercel.app
  - Inspector: https://vercel.com/por-wore/extra-ellipse/DZLPPgpMYDaXZ5gRfczN7bxAdfsq
  - Verified unauthenticated: `/`, `/_astro/index.CdYMa1_A.css`, `/_astro/hero.*.webp` and
    `/favicon.svg` all return 200 with correct content types. HTML contains the Spanish copy,
    `lang="es"`, real `alt` text and responsive `srcset`.
  - Non-blocking warning from Vercel: `engines.node: ">=22.22.0"` auto-upgrades on future Node
    majors. Build succeeded as-is.
