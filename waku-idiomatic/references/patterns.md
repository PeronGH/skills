# Waku Patterns Reference

## Page / Layout / Slice Shape

Every routable file follows the same two-export contract:

```tsx
// ./src/pages/about.tsx
export default async function AboutPage() {
    const data = await getData();
    return (
        <>
            <title>{data.title}</title>
            <h1>{data.headline}</h1>
        </>
    );
}

const getData = async () => ({ title: "About", headline: "About Us" });

export const getConfig = async () => {
    return { render: "static" } as const;
};
```

Slices add an `id` and live in `./src/pages/_slices/`:

```tsx
// ./src/pages/_slices/recommendations.tsx
export default async function Recommendations() {
    return <section>{/* dynamic personalized content */}</section>;
}
export const getConfig = async () => ({ render: "dynamic" }) as const;
```

## Weaving Pattern (Global Providers)

Server layout wraps a client Providers component, passing children through:

```tsx
// ./src/pages/_layout.tsx (server component — no directive)
import "../styles.css";
import { Providers } from "../components/providers";
import { Header } from "../components/header";
import { Footer } from "../components/footer";

export default async function RootLayout({ children }) {
    return (
        <Providers>
            <Header />
            <main>{children}</main>
            <Footer />
        </Providers>
    );
}
export const getConfig = async () => ({ render: "static" }) as const;
```

```tsx
// ./src/components/providers.tsx
"use client";
import { Provider, createStore } from "jotai";

const store = createStore();
export const Providers = ({ children }) => (
    <Provider store={store}>{children}</Provider>
);
```

Children remain server components even though they pass through a client boundary.

## Client Component Boundary

Push `'use client'` to the smallest leaf that needs it:

```tsx
// ./src/components/counter.tsx
"use client";
import { useState } from "react";

export const Counter = () => {
    const [count, setCount] = useState(0);
    return (
        <section>
            <div>Count: {count}</div>
            <button onClick={() => setCount((c) => c + 1)}>Increment</button>
        </section>
    );
};
```

The page that uses it stays a server component:

```tsx
// ./src/pages/index.tsx (no 'use client')
import { Counter } from "../components/counter";

export default async function HomePage() {
    const data = await getData();
    return (
        <div>
            <h1>{data.headline}</h1>
            <Counter />
        </div>
    );
}

export const getConfig = async () => ({ render: "static" }) as const;
```

## Server Actions & Mutations

Inline `'use server'` in a function body, or at the top of a file exporting only action functions:

```tsx
// ./src/lib/actions.ts
"use server";

import { readFile, writeFile } from "node:fs/promises";
import { unstable_rerenderRoute } from "waku/router/server";

export async function addComment(formData: FormData) {
    const comment = formData.get("comment") as string;
    // persist...
    unstable_rerenderRoute("/blog");
}
```

Use with a form (works in both server and client components):

```tsx
<form action={addComment}>
    <input name="comment" required />
    <button type="submit">Post</button>
</form>
```

For pending UI in client components, use `useFormStatus` from `react-dom`:

```tsx
"use client";
import { useFormStatus } from "react-dom";

const SubmitButton = () => {
    const { pending } = useFormStatus();
    return <button disabled={pending}>{pending ? "Saving..." : "Save"}</button>;
};
```

## Segment Routes & Type Safety

```tsx
// ./src/pages/blog/[slug].tsx
import type { PageProps } from "waku/router";

export default async function BlogArticlePage({
    slug,
}: PageProps<"/blog/[slug]">) {
    const article = await getArticle(slug);
    return (
        <>
            <title>{article.title}</title>
            <article>{article.content}</article>
        </>
    );
}

export const getConfig = async () => {
    const staticPaths = await getAllSlugs();
    return { render: "static", staticPaths } as const;
};
```

Nested segments use ordered arrays for static paths:

```tsx
export const getConfig = async () =>
    ({
        render: "static",
        staticPaths: [
            ["electronics", "laptop"],
            ["electronics", "phone"],
        ],
    }) as const;
```

## API Routes

```tsx
// ./src/pages/_api/users/[id].ts
import type { ApiContext } from "waku/router";

export async function GET(
    _req: Request,
    { params }: ApiContext<"/users/[id]">,
) {
    return Response.json({ id: params.id, name: `User ${params.id}` });
}

export async function POST(req: Request) {
    const body = await req.json();
    return Response.json({ created: true, ...body });
}
```

## Slices (Mixed Render / Server Islands)

```tsx
// ./src/pages/product.tsx
import { Slice } from "waku/router/client";

export default async function ProductPage() {
    return (
        <div>
            <Slice id="product-info" />
            <Slice id="reviews" lazy fallback={<p>Loading reviews...</p>} />
        </div>
    );
}

export const getConfig = async () =>
    ({
        render: "static",
        slices: ["product-info"], // lazy slices excluded
    }) as const;
```

## Metadata Component Pattern

```tsx
// ./src/components/meta.tsx
type MetaProps = { title: string; description: string };

export const Meta = ({ title, description }: MetaProps) => (
    <>
        <title>{title}</title>
        <meta name="description" content={description} />
        <meta property="og:title" content={title} />
        <meta property="og:description" content={description} />
    </>
);
```

Use in any page: `<Meta title="Home" description="Welcome" />`

## Root Element (Custom html/head/body)

```tsx
// ./src/pages/_root.tsx
export default async function RootElement({ children }) {
    return (
        <html lang="en">
            <head></head>
            <body>{children}</body>
        </html>
    );
}
export const getConfig = async () => ({ render: "static" }) as const;
```

## Middleware (Hono)

```tsx
// ./src/middleware/no-trailing-slash.ts
import { trimTrailingSlash } from "hono/trailing-slash";
export default () => trimTrailingSlash({ alwaysRedirect: true });
```

For shared request data:

```tsx
// ./src/middleware/auth.ts
import type { MiddlewareHandler } from "hono";
import { unstable_getContextData as getContextData } from "waku/server";

const authMiddleware = (): MiddlewareHandler => async (c, next) => {
    const data = getContextData();
    data.user = await validateSession(c.req.header("cookie"));
    await next();
};
export default authMiddleware;
```

## Group Routes (Layout Scoping)

```
src/pages/
├── index.tsx              # / — no shared layout
├── (marketing)/
│   ├── _layout.tsx        # shared marketing layout
│   ├── about.tsx          # /about
│   └── pricing.tsx        # /pricing
└── (app)/
    ├── _layout.tsx        # shared app layout (dynamic)
    ├── dashboard.tsx      # /dashboard
    └── settings.tsx       # /settings
```

Parenthesized dirs don't affect URLs. Use them to scope layouts and mix render modes.

## Private Directory

```tsx
// Accessible only in server components
import { readFileSync } from "node:fs";

export default async function Page() {
    const config = JSON.parse(readFileSync("./private/config.json", "utf8"));
    return <div>{config.siteName}</div>;
}

export const getConfig = async () => ({ render: "static" }) as const;
```

## Environment Variables

```bash
# .env
DATABASE_URL=postgres://...        # server only
WAKU_PUBLIC_API_BASE=https://...   # accessible in client components
```

Never pass server-only env vars as props to client components.
