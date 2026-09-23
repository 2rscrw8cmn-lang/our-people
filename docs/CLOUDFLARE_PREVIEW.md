# Cloudflare preview setup

The clickable lo-fi prototype is Cloudflare Pages-ready on the `prototype/lofi-interaction` branch.

## One-time Pages setup

In Cloudflare:

1. Open **Workers & Pages**.
2. Choose **Create application** → **Pages** → **Import an existing Git repository**.
3. Select `2rscrw8cmn-lang/our-people`.
4. Use:
   - **Production branch:** `prototype/lofi-interaction`
   - **Framework preset:** None
   - **Build command:** `exit 0`
   - **Build output directory:** `public`
5. Save and deploy.

Cloudflare will provide a `*.pages.dev` URL. The project can later be pointed at `main` when the real application replaces the prototype.

## Why this structure

The prototype source remains in `prototype/` for review. The same static files are copied into `public/` so Cloudflare Pages can deploy them without a framework or build step.

## Prototype behavior

- in-memory only; refresh resets data
- no backend or D1 yet
- mobile-first
- intended only to validate the interaction model
