---
name: nextfriday-code-style
description: Next Friday code style rules for formatting, structure, and readability. Use when writing functions, conditionals, or organizing code.
user-invocable: false
---

# Next Friday Code Style

Rules for code formatting, structure, and readability.

## Control Flow

### Guard Clauses

Use early returns instead of nested if statements.

```typescript
// Bad:
function processData(data: Data | null): Item[] {
  if (data) {
    if (data.items) {
      return data.items.map(formatItem);
    }
  }
  return [];
}

// Good:
function processData(data: Data | null): Item[] {
  if (!data) return [];
  if (!data.items) return [];

  return data.items.map(formatItem);
}
```

### No Nested Ternary

Use functions with early returns instead.

```typescript
// Bad:
const status = isLoading ? "loading" : hasError ? "error" : "success";

// Good:
function getStatus(): string {
  if (isLoading) return "loading";
  if (hasError) return "error";

  return "success";
}
```

## Async Code

### Prefer async/await

No `.then()` promise chains.

```typescript
// Bad:
fetchData(url)
  .then((response) => response.json())
  .then((data) => setData(data));

// Good:
async function loadData(): Promise<void> {
  const response = await fetchData(url);
  const data = await response.json();
  setData(data);
}
```

## Functions

### Function Declarations

Use declarations over arrow functions in `.ts` files.

```typescript
// Bad:
const formatDate = (date: Date): string => {
  return date.toLocaleDateString();
};

// Good:
function formatDate(date: Date): string {
  return date.toLocaleDateString();
}
```

### Separate Exports

Declare first, export after.

```typescript
// Bad:
export function fetchData() {}

// Good:
function fetchData() {}
export { fetchData };
```

## Formatting

### Curly Braces

Single-line: no braces. Multi-line: require braces.

```typescript
// Bad:
if (!data) { return null; }

// Good:
if (!data) return null;
```

### Extract Complexity

Move complex expressions out of return statements and function parameters.

```typescript
// Bad:
return isActive ? "Active" : "Inactive";
processData(value ?? defaultValue);

// Good:
const label = isActive ? "Active" : "Inactive";
return label;

const data = value ?? defaultValue;
processData(data);
```

### Blank Lines

Add blank lines after multi-line blocks and before return statements.

```typescript
// Good:
const config = {
  baseUrl: process.env.API_URL,
  timeout: 5000,
};

const item = items.find((item) => item.id === id);

return item;
```

### Sorted Destructuring

Alphabetical order, defaults first.

```typescript
// Good:
const { count = 0, status = "active", id, name } = data;
```
