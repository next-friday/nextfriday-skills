# Imports

Rules for import statements and module resolution.

## NO_RELATIVE_IMPORTS

Disallow relative imports with parent directory traversal (`../`). Use absolute imports.

```typescript
// Bad: relative imports with ../
import { Button } from "../../../components/Button";
import { formatDate } from "../../utils/format";

// Good: absolute imports
import { Button } from "@/components/Button";
import { formatDate } from "@/utils/format";
import { validate } from "./validate"; // sibling import OK
```

## PREFER_IMPORT_TYPE

Use `import type` for type-only imports.

```typescript
// Bad: regular import for types
import { ReactNode, FC } from "react";
import { User, Item } from "@/types";

// Good: import type
import type { ReactNode, FC } from "react";
import type { User, Item } from "@/types";
```

## NO_DIRECT_DATE

Use centralized date utilities (e.g., dayjs) instead of native Date.

```typescript
// Bad: direct Date usage
const now = new Date();
const timestamp = Date.now();
const parsed = Date.parse("2024-01-01");

// Good: centralized date utility
import dayjs from "dayjs";

const now = dayjs();
const timestamp = dayjs().valueOf();
const parsed = dayjs("2024-01-01");
```

## Quick Reference

| Rule | Pattern |
| ---- | ------- |
| No `../` imports | Use absolute paths or `@/` alias |
| Type imports | `import type { X }` for types |
| Date handling | Use dayjs, not native Date |
