---
name: nextfriday-react
description: Next Friday React/JSX patterns for components, props, and formatting. Use when writing React components or JSX code.
user-invocable: false
---

# Next Friday React/JSX

Rules for React components and JSX patterns.

## Lazy Loading

### Suspense Required

Always wrap lazy-loaded components in Suspense.

```tsx
// Bad:
const Modal = lazy(() => import("./Modal"));
return <Modal isOpen={isOpen} />;

// Good:
const Modal = lazy(() => import("./Modal"));
return (
  <Suspense fallback={<Loading />}>
    <Modal isOpen={isOpen} />
  </Suspense>
);
```

## Props

### No Inline Objects

Extract inline objects in JSX props to const variables.

```tsx
// Bad:
<Card style={{ padding: 16, margin: 8 }} />

// Good:
const cardStyle = { padding: 16, margin: 8 };
<Card style={cardStyle} />
```

### Destructure in Body

Destructure props inside component body, not in parameters.

```tsx
// Bad:
const Card = ({ title, children }: Readonly<CardProps>) => ...

// Good:
const Card = (props: Readonly<CardProps>) => {
  const { title, children } = props;

  return ...
};
```

## Component Structure

### No Helper Functions

Move non-component functions to separate files.

```tsx
// Bad:
const formatPrice = (value: number): string => `$${value.toFixed(2)}`;
const Card = (props: Readonly<CardProps>) => <div>{formatPrice(props.price)}</div>;

// Good:
import { formatPrice } from "@/utils/format";
const Card = (props: Readonly<CardProps>) => <div>{formatPrice(props.price)}</div>;
```

### No Variables in Callbacks

Extract JSX callbacks with variables to render functions.

```tsx
// Bad:
{items.map((item) => {
  const label = `${item.name} - ${item.category}`;
  return <li key={item.id}>{label}</li>;
})}

// Good:
const renderItem = (item: Item) => {
  const label = `${item.name} - ${item.category}`;

  return <li key={item.id}>{label}</li>;
};

return <ul>{items.map(renderItem)}</ul>;
```

## Imports

### Direct React Imports

Import React types directly, not as `React.X`.

```tsx
// Bad:
const Card = (props: { children: React.ReactNode }) => ...

// Good:
import type { ReactNode } from "react";
const Card = (props: { children: ReactNode }) => ...
```

## Formatting

### Newlines Between Elements

Add blank lines between multi-line sibling JSX elements.

```tsx
// Bad:
<section className="header">
  <Title value={title} />
</section>
<section className="content">
  <List items={items} />
</section>

// Good:
<section className="header">
  <Title value={title} />
</section>

<section className="content">
  <List items={items} />
</section>
```

### Template Literals

Use template literals instead of mixing text with expressions.

```tsx
// Bad:
<span>Total: {total}</span>

// Good:
<span>{`Total: ${total}`}</span>
```
