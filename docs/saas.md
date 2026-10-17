# SaaS

> Starter app with marketing pages, sign-in flows and a dashboard.

Page: https://qinyangwang.github.io/ui/docs/saas/

## Installation

```bash
npx shadcn@latest add @qinyang/saas
```

Without the `@qinyang` namespace in components.json:

```bash
npx shadcn@latest add https://qinyangwang.github.io/ui/r/saas.json
```

Packages: `motion`, `simple-icons`.

Registry items it builds on: `@qinyang/theme`, `@qinyang/icons`, `@qinyang/otp-input`, `@qinyang/signup-form`, `@qinyang/avatar`, `@qinyang/button`, `@qinyang/button-stateful`, `@qinyang/checkbox`, `@qinyang/field`, `@qinyang/icon-chip`, `@qinyang/input`, `@qinyang/password-input`, `@qinyang/stat-card`, `@qinyang/theme-toggle`, `@qinyang/drawer`, `@qinyang/badge`, `@qinyang/accordion`, `@qinyang/card`, `@qinyang/marquee`, `@qinyang/number-ticker`, `@qinyang/segmented-control`, `@qinyang/shader-background`, `@qinyang/text-reveal`, `@qinyang/trend-chart`, `@qinyang/not-found-terminal`, `@qinyang/accent-picker`, `@qinyang/toast`, `@qinyang/tooltip`, `@qinyang/page-header`, `@qinyang/settings-section`, `@qinyang/data-table`, `@qinyang/dialog`, `@qinyang/menu`, `@qinyang/radio`, `@qinyang/select`, `@qinyang/switch`, `@qinyang/table`, `@qinyang/textarea`, `@qinyang/usage-meter`, `@qinyang/bar-list`, `@qinyang/date-range-picker`, `@qinyang/donut-chart`, `@qinyang/empty-state`, `@qinyang/command-palette`, `@qinyang/animated-sidebar`, `@qinyang/breadcrumb`, `@qinyang/user-menu`, `@qinyang/alert`, `@qinyang/app-shell`, `@qinyang/brand-icon`, `@qinyang/input-group`, `@qinyang/kbd`.

## Usage

```tsx
// Live preview: /templates/saas (pages under /templates/saas/dashboard, /login, …)
import { HomePage } from "@/registry/base-nova/templates/saas/components/marketing/pages"

export default function SaasDemo() {
  return <HomePage />
}
```
