---
name: waku-idiomatic
description: "Use when writing, reviewing, or scaffolding a Waku project. Trigger on any mention of Waku, waku.gg, or React Server Components in a Waku context. Also trigger when creating new pages, layouts, API routes, or server actions in a project that uses Waku."
---

# Idiomatic Waku

This skill is an opinionated house style for Waku `v1.0.0-alpha.5`.

Grep `references/patterns.md` for concrete examples that follow these rules.

## Core Rules

- Every page, layout, and slice exports two things: a `default` async component and a named `getConfig`. No exceptions.
- Always specify `render: 'static'` or `render: 'dynamic'` explicitly in `getConfig`. Use `as const` on the return.
- Everything is a server component by default. Only add `'use client'` when the component needs state, effects, event handlers, or browser APIs.
- Push `'use client'` as far down the component tree as possible. Never put it on a page or layout file.
- `'use server'` goes on async functions (inline or file-level), never on component files. Each action creates an unsecured endpoint — add auth inside the function body.

## File Structure

- Pages, layouts, slices: `./src/pages/`
- API routes: `./src/pages/_api/` — export named HTTP methods (`GET`, `POST`, etc.)
- Non-routed code inside pages dir: `_components/` and `_hooks/` (ignored by router)
- Server-only data files: `./private/`
- Global styles: import in root `_layout.tsx`

## Rendering Strategy

- Default layouts to `'static'`, pages to whichever fits. A layout and its page can differ.
- Use slices (`<Slice id="..." />`) for mixed-render composition. Use `lazy` + `fallback` for dynamic slices in static pages (server islands pattern). Lazy slices are excluded from the `slices` array in `getConfig`.
- After mutations in server actions, call `unstable_rerenderRoute('/path')` to revalidate.

## Data & State

- Fetch data directly in async server components. No hooks, no client-side fetching needed for server data.
- Use `./private/` for server-only files (accessible via `readFileSync`/`readFile` in server components).
- Prefer Jotai for client state. Wrap in a `'use client'` Providers component, weave via layout children prop.
- Environment variables are private by default. Prefix with `WAKU_PUBLIC_` for client access. Never pass private vars as props to client components.

## Navigation & Typing

- Use `<Link to="/path">` from `waku` for internal links (auto-prefetches).
- Use `useRouter()` from `waku` in client components for programmatic navigation (`push`, `replace`, `back`, `forward`, `reload`, `prefetch`).
- Type route params with `PageProps<'/blog/[slug]'>` from `waku/router`.
- Type API params with `ApiContext<'/users/[id]'>` from `waku/router`.

## Metadata

- Render `<title>`, `<meta>`, `<link>` directly in server components — Waku auto-hoists to `<head>`.
- Extract into a reusable `<Meta title={} description={} />` component for consistency.

## Middleware

- Middleware files export Hono middleware handlers. Waku runs on Hono.
- Use `unstable_getContextData()` from `waku/server` to share data between middleware and server components.

## Anti-Patterns

- Do not put `'use client'` on layout or page files.
- Do not put `'use server'` at the top of a server component file.
- Do not use `getServerSideProps` / `getStaticProps` — those are Next.js. Waku uses `getConfig` + direct async fetching.
- Do not build complex caching layers or deeply nested API hierarchies. Waku is minimal by design — if you're fighting it, you may need a heavier framework.
