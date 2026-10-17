# Recommendation Card

> Shows an agent's suggestion for the user to accept or swap.

Page: https://qinyangwang.github.io/ui/docs/recommendation-card/

## Installation

```bash
npx shadcn@latest add @qinyang/recommendation-card
```

Without the `@qinyang` namespace in components.json:

```bash
npx shadcn@latest add https://qinyangwang.github.io/ui/r/recommendation-card.json
```

Registry items it builds on: `@qinyang/card`, `@qinyang/badge`, `@qinyang/button`.

## Usage

```tsx
import { RecommendationCard } from "@/registry/base-nova/blocks/recommendation-card/recommendation-card"

export default function RecommendationCardDemo() {
  return <RecommendationCard />
}
```
