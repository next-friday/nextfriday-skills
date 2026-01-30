---
name: nextfriday-nextjs
description: Next Friday Next.js rules for environment variables and client components. Use when working with Next.js specific features.
user-invocable: false
---

# Next Friday Next.js

Rules specific to Next.js applications.

## Environment Variables

### Client Components

Client components must use `NEXT_PUBLIC_` prefix for environment variables.

```tsx
// Bad:
"use client";

const apiUrl = process.env.API_URL;
const secretKey = process.env.SECRET_KEY;

// Good:
"use client";

const apiUrl = process.env.NEXT_PUBLIC_API_URL;
const appName = process.env.NEXT_PUBLIC_APP_NAME;
const isDev = process.env.NODE_ENV === "development"; // NODE_ENV is OK
```

### No Fallback Values

Disallow fallback values for environment variables. Fail explicitly instead.

```typescript
// Bad:
const apiUrl = process.env.API_URL || "http://localhost:3000";
const timeout = process.env.TIMEOUT ?? "5000";

// Good:
const apiUrl = process.env.API_URL;
const timeout = process.env.TIMEOUT;

if (!apiUrl) {
  throw new Error("API_URL environment variable is required");
}
```

## Quick Reference

| Rule | Pattern |
| ---- | ------- |
| Client env vars | `NEXT_PUBLIC_` prefix required |
| No env fallbacks | Throw error if missing |
