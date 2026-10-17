# Theme

> Design tokens, type scale and utilities every component in the library reads.

Page: https://qinyangwang.github.io/ui/docs/theme/

## Installation

```bash
npx shadcn@latest add @qinyang/theme
```

Without the `@qinyang` namespace in components.json:

```bash
npx shadcn@latest add https://qinyangwang.github.io/ui/r/theme.json
```

Registry items it builds on: `@qinyang/utils`.

## Usage

```tsx
const surfaces = ["raised", "pressed", "primary", "well", "surface", "chip"] as const

export default function ThemeDemo() {
  return (
    <div className="grid grid-cols-3 gap-4">
      {surfaces.map((s) => (
        <div key={s} className="flex flex-col items-center gap-2">
          <div
            className={
              s === "primary"
                ? "size-16 rounded-2xl bg-primary shadow-primary"
                : "size-16 rounded-2xl bg-card"
            }
            style={s === "primary" ? undefined : { boxShadow: `var(--skeuo-${s})` }}
          />
          <code className="text-xs text-muted-foreground">shadow-{s}</code>
        </div>
      ))}
    </div>
  )
}
```
