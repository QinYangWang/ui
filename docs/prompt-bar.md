# Prompt Bar

> Input where the user writes and sends a prompt to an agent.

Page: https://qinyangwang.github.io/ui/docs/prompt-bar/

## Installation

```bash
npx shadcn@latest add @qinyang/prompt-bar
```

Without the `@qinyang` namespace in components.json:

```bash
npx shadcn@latest add https://qinyangwang.github.io/ui/r/prompt-bar.json
```

Packages: `motion`.

Registry items it builds on: `@qinyang/button`, `@qinyang/icons`.

## Usage

```tsx
"use client"

import * as React from "react"

import { PromptBar } from "@/registry/base-nova/blocks/prompt-bar/prompt-bar"

export default function PromptBarDemo() {
  const [busy, setBusy] = React.useState(false)
  return (
    <PromptBar
      className="max-w-xl"
      busy={busy}
      onStop={() => setBusy(false)}
      onSubmit={() => {
        setBusy(true)
        setTimeout(() => setBusy(false), 2000)
      }}
    />
  )
}
```
