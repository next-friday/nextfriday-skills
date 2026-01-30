# Code Style

Rules for code formatting, structure, and readability.

## PREFER_GUARD_CLAUSE

Use early returns instead of nested if statements.

```typescript
// Bad: nested conditionals
function processData(data: Data | null): Item[] {
  if (data) {
    if (data.items) {
      return data.items.map(formatItem);
    }
  }
  return [];
}

// Good: guard clauses
function processData(data: Data | null): Item[] {
  if (!data) return [];
  if (!data.items) return [];

  return data.items.map(formatItem);
}
```

## PREFER_ASYNC_AWAIT

Use async/await over `.then()` promise chains.

```typescript
// Bad: promise chains
fetchData(url)
  .then((response) => response.json())
  .then((data) => setData(data));

// Good: async/await
async function loadData(): Promise<void> {
  const response = await fetchData(url);
  const data = await response.json();
  setData(data);
}
```

## PREFER_FUNCTION_DECLARATION

Use function declarations over arrow functions in `.ts` files.

```typescript
// Bad: arrow function variable
const formatDate = (date: Date): string => {
  return date.toLocaleDateString();
};

// Good: function declaration
function formatDate(date: Date): string {
  return date.toLocaleDateString();
}
```

## ENFORCE_CURLY_NEWLINE

Single-line statements: no braces. Multi-line statements: require braces.

```typescript
// Bad: inconsistent curly braces
if (!data) { return null; }
if (isLoading && hasError) return null;

// Good: consistent curly braces
if (!data) return null;
if (isLoading && hasError) {
  return null;
}
```

## NO_NESTED_TERNARY

Avoid nested ternary expressions. Use functions with early returns.

```typescript
// Bad: nested ternary
const status = isLoading ? "loading" : hasError ? "error" : "success";

// Good: function with early returns
function getStatus(): string {
  if (isLoading) return "loading";
  if (hasError) return "error";

  return "success";
}
```

## NO_COMPLEX_INLINE_RETURN

Extract complex expressions from return statements.

```typescript
// Bad: complex inline return
function getLabel(isActive: boolean): string {
  return isActive ? "Active" : "Inactive";
}

// Good: extracted to variable
function getLabel(isActive: boolean): string {
  const label = isActive ? "Active" : "Inactive";

  return label;
}
```

## NO_LOGIC_IN_PARAMS

Extract logic from function parameters to variables.

```typescript
// Bad: logic in params
processData(value ?? defaultValue);
updateUser(isAdmin ? adminUser : regularUser);

// Good: extracted to variable
const data = value ?? defaultValue;
processData(data);

const user = isAdmin ? adminUser : regularUser;
updateUser(user);
```

## NO_INLINE_DEFAULT_EXPORT

Separate declarations from exports.

```typescript
// Bad: inline export
export function fetchData() {}
export default function processData() {}

// Good: separate declaration and export
function fetchData() {}
function processData() {}

export { fetchData };
export default processData;
```

## NO_INLINE_NESTED_OBJECT

Nested objects and arrays must span multiple lines.

```typescript
// Bad: inline nested object
const config = {
  api: { baseUrl: "https://api.example.com", timeout: 5000 },
};

// Good: multi-line nested object
const config = {
  api: {
    baseUrl: "https://api.example.com",
    timeout: 5000,
  },
};
```

## ENFORCE_SORTED_DESTRUCTURING

Sort destructuring properties alphabetically. Default values first.

```typescript
// Bad: unsorted destructuring
const { name, id, status = "active", count = 0 } = data;

// Good: sorted, defaults first
const { count = 0, status = "active", id, name } = data;
```

## NEWLINE_AFTER_MULTILINE_BLOCK

Require blank line after multi-line statements.

```typescript
// Bad: no blank line
const config = {
  baseUrl: process.env.API_URL,
  timeout: 5000,
};
const data = fetchData(config);

// Good: blank line after multi-line block
const config = {
  baseUrl: process.env.API_URL,
  timeout: 5000,
};

const data = fetchData(config);
```

## NEWLINE_BEFORE_RETURN

Require blank line before return statements (when other statements exist).

```typescript
// Bad: no blank line before return
function findById(items: Item[], id: string): Item | null {
  const item = items.find((item) => item.id === id);
  return item ?? null;
}

// Good: blank line before return
function findById(items: Item[], id: string): Item | null {
  const item = items.find((item) => item.id === id);

  return item ?? null;
}
```

## NO_EMOJI

Prevent emoji characters in source code.

```typescript
// Bad: emoji in code
const message = "Success! 🎉";
const status = "Loading... ⏳";

// Good: no emoji
const message = "Success!";
const status = "Loading...";
```

## Quick Reference

| Rule | Pattern |
| ---- | ------- |
| Guard clauses | Early returns, avoid nesting |
| Async/await | No `.then()` chains |
| Function declaration | Not arrow functions in .ts |
| Curly braces | Single-line: none, Multi-line: required |
| No nested ternary | Use functions instead |
| Extract complexity | Variables before return |
| No logic in params | Extract to variables |
| Separate exports | Declare first, export after |
| Multi-line nested | Objects on separate lines |
| Sorted destructuring | Alphabetical, defaults first |
| Blank lines | After multi-line, before return |
