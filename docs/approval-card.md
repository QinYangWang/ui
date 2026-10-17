# Approval Card

> Asks the user to approve or decline an agent's action.

Page: https://qinyangwang.github.io/ui/docs/approval-card/

## Installation

```bash
npx shadcn@latest add @qinyang/approval-card
```

Without the `@qinyang` namespace in components.json:

```bash
npx shadcn@latest add https://qinyangwang.github.io/ui/r/approval-card.json
```

Packages: `motion`.

Registry items it builds on: `@qinyang/card`, `@qinyang/badge`, `@qinyang/button`, `@qinyang/icons`, `@qinyang/icon-chip`.

## Usage

```tsx
import { ApprovalCard } from "@/registry/base-nova/blocks/approval-card/approval-card"

export default function ApprovalCardDemo() {
  return <ApprovalCard />
}
```
