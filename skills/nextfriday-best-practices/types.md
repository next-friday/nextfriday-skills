# Types

Rules for TypeScript type definitions and annotations.

## ENFORCE_PROPS_SUFFIX

Interfaces and type aliases in React component files must end with `Props`.

```tsx
// Bad: missing Props suffix
// Card.tsx
interface Card {}
type CardOptions = { variant: string };

// Good: Props suffix
// Card.tsx
interface CardProps {}
type CardOptionsProps = { variant: string };
```

## ENFORCE_READONLY_COMPONENT_PROPS

React component props must be wrapped with `Readonly<>`.

```tsx
// Bad: mutable props
interface CardProps {
  title: string;
  children: ReactNode;
}
const Card = (props: CardProps) => <div>{props.children}</div>;

// Good: Readonly props
interface CardProps {
  title: string;
  children: ReactNode;
}
const Card = (props: Readonly<CardProps>) => <div>{props.children}</div>;
```

## PREFER_INTERFACE_OVER_INLINE_TYPES

Use interface declarations for React component props, not inline types.

```tsx
// Bad: inline type annotation
const Card = (props: { title: string; children: ReactNode; onClick: () => void }) => {
  return <div onClick={props.onClick}>{props.children}</div>;
};

// Good: interface declaration
interface CardProps {
  title: string;
  children: ReactNode;
  onClick: () => void;
}

const Card = (props: Readonly<CardProps>) => {
  return <div onClick={props.onClick}>{props.children}</div>;
};
```

## PREFER_NAMED_PARAM_TYPES

Extract inline object types for function parameters into named interfaces.

```typescript
// Bad: inline object type
function processData({ id, name }: { id: string; name: string }) {}

// Good: named interface
interface ProcessDataParams {
  id: string;
  name: string;
}

function processData(params: ProcessDataParams) {}
```

## PREFER_DESTRUCTURING_PARAMS

Use object destructuring for functions with multiple parameters.

```typescript
// Bad: positional parameters
function createItem(id: string, name: string, price: number, category: string) {}

// Good: object destructuring
interface CreateItemParams {
  id: string;
  name: string;
  price: number;
  category: string;
}

function createItem(params: CreateItemParams) {}
```

## REQUIRE_EXPLICIT_RETURN_TYPE

Require explicit return types on functions.

```typescript
// Bad: implicit return type
function formatValue(value: number) {
  return value.toFixed(2);
}

async function fetchData(id: string) {
  return await api.get(`/data/${id}`);
}

// Good: explicit return type
function formatValue(value: number): string {
  return value.toFixed(2);
}

async function fetchData(id: string): Promise<Data> {
  return await api.get(`/data/${id}`);
}
```

## Quick Reference

| Rule | Pattern |
| ---- | ------- |
| Props suffix | `CardProps`, not `Card` |
| Readonly props | `props: Readonly<Props>` |
| No inline types | Use interfaces for props |
| Named param types | Extract to interfaces |
| Destructuring | `(params: Params)` not `(a, b, c)` |
| Explicit return | `: string`, `: Promise<Data>` |
