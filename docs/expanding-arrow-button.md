# Expanding Arrow Button

> Call-to-action button with an arrow sweep on hover.

Page: https://qinyangwang.github.io/ui/docs/expanding-arrow-button/

## Installation

```bash
npx shadcn@latest add @qinyang/expanding-arrow-button
```

Without the `@qinyang` namespace in components.json:

```bash
npx shadcn@latest add https://qinyangwang.github.io/ui/r/expanding-arrow-button.json
```

Packages: `@base-ui/react`.

Registry items it builds on: `@qinyang/theme`.

## Usage

```tsx
import { ExpandingArrowButton } from "@/components/ui/expanding-arrow-button"
```

```tsx
<ExpandingArrowButton>Continue to checkout</ExpandingArrowButton>
```

## Examples

### Accents

Use token classes in `accentClassName` for a different accent, and in `labelClassName` for cases like `tabular-nums` on a count.

```tsx
import { ExpandingArrowButton } from "@/registry/base-nova/ui/expanding-arrow-button"

export default function ExpandingArrowButtonAccents() {
  return (
    <div className="flex flex-col items-center gap-3">
      <ExpandingArrowButton accentClassName="bg-foreground text-background">Read the changelog</ExpandingArrowButton>
      <ExpandingArrowButton accentClassName="bg-warning text-black">Review open issues</ExpandingArrowButton>
      <ExpandingArrowButton accentClassName="bg-destructive text-white">Go to danger zone</ExpandingArrowButton>
      <ExpandingArrowButton labelClassName="tabular-nums">Resolve 12 comments</ExpandingArrowButton>
    </div>
  )
}
```

### As Link

Use `render` with `nativeButton={false}` when the button navigates, to render an anchor or router `Link`.

```tsx
import { ExpandingArrowButton } from "@/registry/base-nova/ui/expanding-arrow-button"

export default function ExpandingArrowButtonAsLink() {
  return (
    <ExpandingArrowButton nativeButton={false} render={<a href="#pricing" />}>
      See pricing plans
    </ExpandingArrowButton>
  )
}
```

### Disabled

```tsx
import { ExpandingArrowButton } from "@/registry/base-nova/ui/expanding-arrow-button"

export default function ExpandingArrowButtonDisabled() {
  return <ExpandingArrowButton disabled>Continue (fill in all fields)</ExpandingArrowButton>
}
```

## Motion

The sweep runs on hover and on keyboard focus, over 500ms. With reduced motion the tile changes width instantly and nothing slides.

## API Reference

Built on [the Button primitive](https://base-ui.com/react/components/button#api-reference). Only the props this library adds or changes are listed; everything else passes through.

### ExpandingArrowButton

Button whose accent tile sweeps across on hover or focus. Also accepts every prop of [Button](https://base-ui.com/react/components/button#api-reference).

| Prop | Type | Default | Description |
| --- | --- | --- | --- |
| `accentClassName` | `string` | — | Classes for the accent tile (e.g. a different background). |
| `labelClassName` | `string` | — | Classes for the label. |
