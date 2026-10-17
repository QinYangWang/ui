# Chat App

> Agent workspace with a sidebar, conversation and prompt bar.

Page: https://qinyangwang.github.io/ui/docs/chat-app/

## Installation

```bash
npx shadcn@latest add @qinyang/chat-app
```

Without the `@qinyang` namespace in components.json:

```bash
npx shadcn@latest add https://qinyangwang.github.io/ui/r/chat-app.json
```

Packages: `motion`, `@base-ui/react`.

Registry items it builds on: `@qinyang/theme`, `@qinyang/icons`, `@qinyang/button`, `@qinyang/chat`, `@qinyang/prompt-bar`, `@qinyang/ai-sidebar`, `@qinyang/todo-list`, `@qinyang/reasoning-text`, `@qinyang/agent-progress`, `@qinyang/icon-chip`.

## Usage

```tsx
import { ChatApp } from "@/registry/base-nova/blocks/chat-app/chat-app"

export default function ChatAppDemo() {
  return (
    <div className="h-160 w-full">
      <ChatApp searchHotkey={null} autoPlayPrompt="Plan a Kyoto trip in November" />
    </div>
  )
}
```
