# Bar List

> Ranks items by one measure with a bar behind each label.

Page: https://qinyangwang.github.io/ui/docs/bar-list/

## Installation

```bash
npx shadcn@latest add @qinyang/bar-list
```

Without the `@qinyang` namespace in components.json:

```bash
npx shadcn@latest add https://qinyangwang.github.io/ui/r/bar-list.json
```

Packages: `motion`.

Registry items it builds on: `@qinyang/theme`.

## Usage

```tsx
import { BarList } from "@/components/ui/bar-list"
```

```tsx
<BarList items={[{ name: "/pricing", value: 18420 }, { name: "/", value: 15210 }]} labels={["Page", "Visitors"]} />
```

## Examples

### Colour and Icons

Use `icon` and `href` when each row leads to its own detail page.

```tsx
"use client"

import { GithubIcon, GlobeIcon } from "@/components/icons"
import { BarList } from "@/registry/base-nova/ui/bar-list"

export default function BarListColors() {
  return (
    <div className="w-full max-w-md">
      <BarList
        color={2}
        labels={["Source", "Sign-ups"]}
        items={[
          { name: "github.com", value: 1284, icon: <GithubIcon /> },
          { name: "google.com", value: 1021, icon: <GlobeIcon /> },
          { name: "news.ycombinator.com", value: 642, icon: <GlobeIcon /> },
        ]}
      />
    </div>
  )
}
```

## When to use

Use it for a ranked breakdown of one measure, such as top pages or referrers. It sorts largest first unless `sort="none"`, and under reduced motion the bars appear without growing.

## API Reference

### BarList

Also accepts every prop of `ul`.

| Prop | Type | Default | Description |
| --- | --- | --- | --- |
| `items` (required) | `{ name: string; value: number; icon?: ReactNode; href?: string }[]` | — | Rows. |
| `formatValue` | `(value: number) => string` | — | Number format. |
| `sort` | `"desc" \| "none"` | `"desc"` | Order. |
| `color` | `1 \| 2 \| 3 \| 4 \| 5 \| 6 \| 7 \| 8` | `4` | Chart token (1–8) for the bars. |
| `labels` | `[string, string]` | — | Column headings. |
