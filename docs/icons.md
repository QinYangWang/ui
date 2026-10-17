# Icons

> Rounded outline icon set used across the library.

Page: https://qinyangwang.github.io/ui/docs/icons/

## Installation

```bash
npx shadcn@latest add @qinyang/icons
```

Without the `@qinyang` namespace in components.json:

```bash
npx shadcn@latest add https://qinyangwang.github.io/ui/r/icons.json
```

## Usage

```tsx
import { BellIcon, BotIcon, HeartIcon, SearchIcon, SendIcon, SparklesIcon } from "@/components/icons"

export default function IconsDemo() {
  return (
    <div className="flex items-center gap-5 text-foreground">
      <HeartIcon />
      <SearchIcon />
      <SparklesIcon />
      <BotIcon size={24} />
      <BellIcon className="text-primary" />
      <SendIcon className="text-success rtl:-scale-x-100" />
    </div>
  )
}
```
