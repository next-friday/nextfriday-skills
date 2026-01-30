# File Naming

Rules for naming files based on their type and purpose.

## FILE_KEBAB_CASE

Enforce kebab-case for TypeScript (.ts) and JavaScript (.js) files.

```text
// Bad: other casing styles
UserService.ts
dataUtils.ts
API_helpers.js

// Good: kebab-case
user-service.ts
data-utils.ts
api-helpers.js
```

## JSX_PASCAL_CASE

Enforce PascalCase for JSX (.jsx) and TSX (.tsx) files.

```text
// Bad: non-PascalCase
user-card.tsx
itemList.tsx
button-primary.jsx

// Good: PascalCase
UserCard.tsx
ItemList.tsx
ButtonPrimary.jsx
```

## MD_FILENAME_CASE_RESTRICTION

Enforce SNAKE_CASE (uppercase) for Markdown (.md) files.

```text
// Bad: lowercase or kebab-case
readme.md
getting-started.md
api-reference.md

// Good: SNAKE_CASE uppercase
README.md
GETTING_STARTED.md
API_REFERENCE.md
```

## ENFORCE_HOOK_NAMING

Enforce `use` prefix for functions in custom hook files (`*.hook.ts`, `*.hooks.ts`).

```typescript
// Bad: missing use prefix
// form.hook.ts
export function formValidation() {}
export const dataFetcher = () => {};

// Good: use prefix
// form.hook.ts
export function useFormValidation() {}
export const useDataFetcher = () => {};
```

## Quick Reference

| File Type | Convention | Example |
| --------- | ---------- | ------- |
| .ts / .js | kebab-case | `user-service.ts` |
| .tsx / .jsx | PascalCase | `UserCard.tsx` |
| .md | SNAKE_CASE | `README.md` |
| *.hook.ts | `use` prefix | `useForm()` |
