# Sparkline

> Small inline chart that shows a trend.

Page: https://qinyangwang.github.io/ui/docs/sparkline/

## Installation

```bash
npx shadcn@latest add @qinyang/sparkline
```

Without the `@qinyang` namespace in components.json:

```bash
npx shadcn@latest add https://qinyangwang.github.io/ui/r/sparkline.json
```

Packages: `motion`.

Registry items it builds on: `@qinyang/theme`.

## Usage

```tsx
import { Sparkline } from "@/components/ui/sparkline"
```

```tsx
<Sparkline values={[12, 14, 13, 17, 19, 22]} label="Revenue, up 83%" className="h-8 w-24 text-success" />
```

## Examples

### Variants

Use `bar` for discrete counts and `area` or `line` for continuous trends.

```tsx
import { Sparkline } from "@/registry/base-nova/ui/sparkline"

const values = [4, 6, 5, 8, 7, 9, 12, 10, 13, 15]

export default function SparklineVariants() {
  return (
    <div className="grid w-full max-w-sm grid-cols-3 gap-4">
      {(["area", "line", "bar"] as const).map((v) => (
        <div key={v} className="flex flex-col gap-2">
          <div className="text-chart-1"><Sparkline values={values} variant={v} className="h-10" /></div>
          <span className="text-center text-xs text-muted-foreground">{v}</span>
        </div>
      ))}
    </div>
  )
}
```

## Colour and size

The chart draws in `currentColor`, so tint it with a text token (`text-success`, `text-chart-1`). It stretches to its box, so size it with `h-*` and `w-*` (default 36px tall, full width).

## Accessibility

With `label` it is an `img` with that name; without one it is decorative (`aria-hidden`). Put the number it summarises in text next to it.

## API Reference

### Sparkline

Also accepts every prop of `svg`.

| Prop | Type | Default | Description |
| --- | --- | --- | --- |
| `values` (required) | `readonly number[]` | — | The series, oldest first. |
| `variant` | `"area" \| "line" \| "bar"` | `"area"` | Shape. |
| `label` | `string` | — | Accessible summary. Omit to make the chart decorative. |
| `animate` | `boolean` | `true` | Draw in on mount (always off under reduced motion). |
