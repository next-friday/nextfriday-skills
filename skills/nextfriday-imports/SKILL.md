---
name: nextfriday-imports
description: Next Friday import rules for absolute paths, type imports, and date utilities. Use when adding import statements or working with modules.
user-invocable: false
---

# Next Friday Imports

Rules for import statements and module resolution.

## Absolute Imports

Disallow relative imports with `../`. Use absolute imports instead.

```typescript
// Bad:
import { Button } from "../../../components/Button";
import { formatDate } from "../../utils/format";

// Good:
import { Button } from "@/components/Button";
import { formatDate } from "@/utils/format";
import { validate } from "./validate"; // sibling import OK
```

## Type Imports

Use `import type` for type-only imports.

```typescript
// Bad:
import { ReactNode, FC } from "react";
import { User, Item } from "@/types";

// Good:
import type { ReactNode, FC } from "react";
import type { User, Item } from "@/types";
```

## Date Utilities

Use centralized date utilities (e.g., dayjs) instead of native Date.

```typescript
// Bad:
const now = new Date();
const timestamp = Date.now();

// Good:
import dayjs from "dayjs";

const now = dayjs();
const timestamp = dayjs().valueOf();
```

## Quick Reference

| Rule | Pattern |
| ---- | ------- |
| No `../` imports | Use absolute paths or `@/` alias |
| Type imports | `import type { X }` for types |
| Date handling | Use dayjs, not native Date |
