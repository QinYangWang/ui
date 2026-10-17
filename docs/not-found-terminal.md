# 404 Terminal

> 404 page styled as a terminal session.

Page: https://qinyangwang.github.io/ui/docs/not-found-terminal/

## Installation

```bash
npx shadcn@latest add @qinyang/not-found-terminal
```

Without the `@qinyang` namespace in components.json:

```bash
npx shadcn@latest add https://qinyangwang.github.io/ui/r/not-found-terminal.json
```

Packages: `motion`.

Registry items it builds on: `@qinyang/theme`, `@qinyang/button`.

## Usage

```tsx
import { NotFoundTerminal } from "@/registry/base-nova/blocks/not-found-terminal/not-found-terminal"

export default function NotFoundTerminalDemo() {
  return <NotFoundTerminal homeHref="#" secondaryHref="#" secondaryLabel="Browse docs" />
}
```
