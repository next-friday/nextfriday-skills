# React/JSX

Rules for React components and JSX patterns.

## JSX_REQUIRE_SUSPENSE

Wrap lazy-loaded components in Suspense boundaries.

```tsx
// Bad: lazy component without Suspense
const Modal = lazy(() => import("./Modal"));

return <Modal isOpen={isOpen} />;

// Good: wrapped in Suspense
const Modal = lazy(() => import("./Modal"));

return (
  <Suspense fallback={<Loading />}>
    <Modal isOpen={isOpen} />
  </Suspense>
);
```

## JSX_NO_INLINE_OBJECT_PROP

Extract inline objects in JSX props to const variables.

```tsx
// Bad: inline object props
<Card style={{ padding: 16, margin: 8 }} />
<List data={{ items: items, total: total }} />

// Good: extracted to variables
const cardStyle = { padding: 16, margin: 8 };
<Card style={cardStyle} />

const listData = { items: items, total: total };
<List data={listData} />
```

## JSX_NO_NON_COMPONENT_FUNCTION

Move non-component functions out of component files.

```tsx
// Bad: helper function in component file
const formatPrice = (value: number): string => `$${value.toFixed(2)}`;

const Card = (props: Readonly<CardProps>) => {
  return <div>{formatPrice(props.price)}</div>;
};

// Good: import from separate file
import { formatPrice } from "@/utils/format";

const Card = (props: Readonly<CardProps>) => {
  return <div>{formatPrice(props.price)}</div>;
};
```

## JSX_NO_VARIABLE_IN_CALLBACK

Extract JSX callbacks with variable declarations to render functions.

```tsx
// Bad: variable in callback
<ul>
  {items.map((item) => {
    const label = `${item.name} - ${item.category}`;
    return <li key={item.id}>{label}</li>;
  })}
</ul>

// Good: extracted render function
const renderItem = (item: Item) => {
  const label = `${item.name} - ${item.category}`;

  return <li key={item.id}>{label}</li>;
};

return <ul>{items.map(renderItem)}</ul>;
```

## REACT_PROPS_DESTRUCTURE

Destructure props inside component body, not in parameters.

```tsx
// Bad: destructure in parameters
const Card = ({ title, children, onClick }: Readonly<CardProps>) => {
  return <div onClick={onClick}>{children}</div>;
};

// Good: destructure in body
const Card = (props: Readonly<CardProps>) => {
  const { title, children, onClick } = props;

  return <div onClick={onClick}>{children}</div>;
};
```

## PREFER_REACT_IMPORT_TYPES

Import React types directly, not as `React.X`.

```tsx
// Bad: React.X notation
const Card = (props: { children: React.ReactNode }) => {
  const [isOpen, setIsOpen] = React.useState(false);

  return <div>{props.children}</div>;
};

// Good: direct imports
import type { ReactNode } from "react";
import { useState } from "react";

const Card = (props: { children: ReactNode }) => {
  const [isOpen, setIsOpen] = useState(false);

  return <div>{props.children}</div>;
};
```

## JSX_NEWLINE_BETWEEN_ELEMENTS

Add blank lines between multi-line sibling JSX elements.

```tsx
// Bad: no blank line between multi-line elements
<section className="header">
  <Title value={title} />
</section>
<section className="content">
  <List items={items} />
</section>

// Good: blank line between
<section className="header">
  <Title value={title} />
</section>

<section className="content">
  <List items={items} />
</section>
```

## PREFER_JSX_TEMPLATE_LITERALS

Use template literals instead of mixing text with expressions.

```tsx
// Bad: mixed text and expressions
<span>Total: {total}</span>
<div>Items: {count}</div>

// Good: template literals
<span>{`Total: ${total}`}</span>
<div>{`Items: ${count}`}</div>
```

## Quick Reference

| Rule | Pattern |
| ---- | ------- |
| Suspense | Always wrap lazy components |
| No inline objects | Extract to const |
| No helper functions | Move to separate files |
| No vars in callbacks | Use render functions |
| Props destructure | In body, not params |
| React imports | Direct, not `React.X` |
| JSX newlines | Between multi-line siblings |
| Template literals | `{`Total: ${total}`}` |
