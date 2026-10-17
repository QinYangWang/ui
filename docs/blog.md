# Personal Blog

> Personal blog with a post list and an article page.

Page: https://qinyangwang.github.io/ui/docs/blog/

## Installation

```bash
npx shadcn@latest add @qinyang/blog
```

Without the `@qinyang` namespace in components.json:

```bash
npx shadcn@latest add https://qinyangwang.github.io/ui/r/blog.json
```

Packages: `motion`, `simple-icons`.

Registry items it builds on: `@qinyang/theme`, `@qinyang/typeset`, `@qinyang/badge`, `@qinyang/button`, `@qinyang/icons`, `@qinyang/input`, `@qinyang/scroll-progress`, `@qinyang/theme-toggle`, `@qinyang/toast`, `@qinyang/brand-icon`, `@qinyang/code-block`, `@qinyang/outline`, `@qinyang/cover-art`.

## Usage

```tsx
// app/blog/page.tsx and app/blog/post/page.tsx: each route renders one page of the template.
// Pass hrefs if your blog lives somewhere other than /blog. Live preview: /templates/blog
import { BlogHome } from "@/registry/base-nova/templates/blog/blog"
import { BlogPost } from "@/registry/base-nova/templates/blog/post"

const hrefs = { home: "/blog", post: "/blog/post" }

export function BlogPostDemo() {
  return <BlogPost hrefs={hrefs} />
}

export default function BlogDemo() {
  return <BlogHome hrefs={hrefs} />
}
```
