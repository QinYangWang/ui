# Empty State

> Tells users a list or page is empty and what to do.

Page: https://qinyangwang.github.io/ui/docs/empty-state/

## Installation

```bash
npx shadcn@latest add @qinyang/empty-state
```

Without the `@qinyang` namespace in components.json:

```bash
npx shadcn@latest add https://qinyangwang.github.io/ui/r/empty-state.json
```

Packages: `class-variance-authority`.

Registry items it builds on: `@qinyang/theme`.

## Usage

```tsx
import {
  EmptyState,
  EmptyStateActions,
  EmptyStateDescription,
  EmptyStateIcon,
  EmptyStateTitle,
} from "@/components/ui/empty-state"
```

```tsx
<EmptyState variant="outline">
  <EmptyStateIcon><InboxIcon /></EmptyStateIcon>
  <EmptyStateTitle>No invoices yet</EmptyStateTitle>
  <EmptyStateDescription>Invoices appear here after the first charge.</EmptyStateDescription>
  <EmptyStateActions><Button size="sm">Create invoice</Button></EmptyStateActions>
</EmptyState>
```

## Composition

```text
EmptyState
├── EmptyStateIcon
├── EmptyStateTitle
├── EmptyStateDescription
└── EmptyStateActions
```

## Examples

### Variants

Use `default` inside a card or table, `outline` as a drop zone, and `muted` to set the area apart from the page.

```tsx
import { SearchIcon } from "@/components/icons"
import { EmptyState, EmptyStateDescription, EmptyStateIcon, EmptyStateTitle } from "@/registry/base-nova/ui/empty-state"

export default function EmptyStateVariants() {
  return (
    <div className="grid w-full max-w-2xl grid-cols-1 gap-4 sm:grid-cols-3">
      {(["default", "outline", "muted"] as const).map((v) => (
        <EmptyState key={v} variant={v} size="sm">
          <EmptyStateIcon>
            <SearchIcon />
          </EmptyStateIcon>
          <EmptyStateTitle>No results</EmptyStateTitle>
          <EmptyStateDescription>{v}</EmptyStateDescription>
        </EmptyState>
      ))}
    </div>
  )
}
```

## Writing

Say what is missing, then what to do about it, then offer the action. For a filtered list, say no results matched and offer to clear the filters, as DataTable does.

## API Reference

### EmptyState

Also accepts every prop of `div`.

| Prop | Type | Default | Description |
| --- | --- | --- | --- |
| `variant` | `"default" \| "outline" \| "muted"` | `"default"` | Surface. |
| `size` | `"sm" \| "default" \| "lg"` | `"default"` | Vertical padding. |

### EmptyStateIcon

40px raised chip with a 20px muted glyph. Also accepts every prop of `div`.
