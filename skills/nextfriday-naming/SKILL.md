---
name: nextfriday-naming
description: Next Friday naming conventions for variables, constants, files, hooks, and services. Use when writing or reviewing code that involves naming identifiers.
user-invocable: false
---

# Next Friday Naming Conventions

Rules for naming variables, constants, and files.

## Variable Naming

### Boolean Prefix

Boolean variables must use prefixes: `is`, `has`, `should`, `can`, `did`, `will`

```typescript
// Bad:
const loading = true;
const visible: boolean = true;

// Good:
const isLoading = true;
const isVisible: boolean = true;
```

### Constant Case

Constants with primitive values use SCREAMING_SNAKE_CASE.

```typescript
// Bad:
const apiUrl = "https://api.example.com";
const maxRetries = 3;

// Good:
const API_URL = "https://api.example.com";
const MAX_RETRIES = 3;
```

### Meaningful Names

No lazy identifiers (`xxx`, `asdf`) or single characters (except `i`, `j`, `k`, `n`, `_`).

```typescript
// Bad:
const xxx = "value";
items.map((x) => x.id);

// Good:
const userName = "value";
items.map((item) => item.id);
```

### Service Functions

Async functions in `*.service.ts` use `fetch` prefix.

```typescript
// Bad: user.service.ts
export async function getUsers() {}

// Good: user.service.ts
export async function fetchUsers() {}
```

## File Naming

| File Type | Convention | Example |
| --------- | ---------- | ------- |
| .ts / .js | kebab-case | `user-service.ts` |
| .tsx / .jsx | PascalCase | `UserCard.tsx` |
| .md | SNAKE_CASE | `README.md` |
| *.hook.ts | `use` prefix | `useForm()` |
