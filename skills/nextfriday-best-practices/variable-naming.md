# Variable Naming

Rules for naming variables, constants, and identifiers.

## BOOLEAN_NAMING_PREFIX

Enforce boolean variables and parameters to have a prefix like `is`, `has`, `should`, `can`, `did`, `will`.

```typescript
// Bad: unclear boolean intent
const loading = true;
const error = false;
const visible: boolean = true;
function toggle(active: boolean) {}

// Good: clear boolean prefix
const isLoading = true;
const hasError = false;
const isVisible: boolean = true;
function toggle(isActive: boolean) {}
```

## ENFORCE_CONSTANT_CASE

Ensure `const` declarations with primitive values use SCREAMING_SNAKE_CASE.

```typescript
// Bad: lowercase constants
const apiUrl = "https://api.example.com";
const maxRetries = 3;
const defaultTimeout = 5000;

// Good: SCREAMING_SNAKE_CASE
const API_URL = "https://api.example.com";
const MAX_RETRIES = 3;
const DEFAULT_TIMEOUT = 5000;
```

## NO_LAZY_IDENTIFIERS

Disallow lazy, meaningless variable names (repeated characters 3+, keyboard sequences 4+).

```typescript
// Bad: lazy identifiers
const xxx = "value";
const asdf = getData();
function qwerty() {}

// Good: meaningful names
const userName = "value";
const userData = getData();
function validateInput() {}
```

## NO_SINGLE_CHAR_VARIABLES

Disallow single character identifiers except loop counters (`i`, `j`, `k`, `n`) and underscore (`_`).

```typescript
// Bad: single character variables
const d = new Date();
const u = await fetchUser();
items.map((x) => x.id);

// Good: descriptive names
const createdAt = new Date();
const user = await fetchUser();
items.map((item) => item.id);
```

## ENFORCE_SERVICE_NAMING

Enforce `fetch` prefix for async functions in `*.service.ts` files.

```typescript
// Bad: get/load prefix in service files
// user.service.ts
export async function getUsers() {}
export async function loadUserById(id: string) {}

// Good: fetch prefix in service files
// user.service.ts
export async function fetchUsers() {}
export async function fetchUserById(id: string) {}
```

## Quick Reference

| Rule | Pattern |
| ---- | ------- |
| Booleans | `is`, `has`, `should`, `can`, `did`, `will` prefix |
| Constants | SCREAMING_SNAKE_CASE |
| No lazy names | Avoid `xxx`, `asdf`, keyboard patterns |
| No single char | Use descriptive names (except `i`, `j`, `k`, `n`, `_`) |
| Service files | `fetch` prefix for async functions |
