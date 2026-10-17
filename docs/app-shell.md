# App Shell

> App frame with a header, rail sidebar and inset content panel.

Page: https://qinyangwang.github.io/ui/docs/app-shell/

## Installation

```bash
npx shadcn@latest add @qinyang/app-shell
```

Without the `@qinyang` namespace in components.json:

```bash
npx shadcn@latest add https://qinyangwang.github.io/ui/r/app-shell.json
```

Packages: `@base-ui/react`, `motion`.

Registry items it builds on: `@qinyang/theme`, `@qinyang/icons`, `@qinyang/animated-sidebar`, `@qinyang/drawer`.

## Usage

```tsx
import { AppShell, AppShellHeader, AppShellMain, AppShellSidebar } from "@/components/ui/app-shell"
import { SidebarContent, SidebarItem, SidebarMenu } from "@/components/ui/animated-sidebar"
```

```tsx
<AppShell>
  <AppShellHeader>
    <span className="text-ui font-semibold">Acme</span>
  </AppShellHeader>
  <AppShellSidebar>
    <SidebarContent>
      <SidebarMenu>
        <SidebarItem icon={<HomeIcon />} label="Home" isActive />
      </SidebarMenu>
    </SidebarContent>
  </AppShellSidebar>
  <AppShellMain>
    <div className="p-8">…</div>
  </AppShellMain>
</AppShell>
```

## Composition

```text
AppShell
├── AppShellHeader
│   └── AppShellTrigger
├── AppShellSidebar
│   └── SidebarContent, SidebarFooter, …
└── AppShellMain
```

## Examples

### Icon Rail

Use `defaultOpen={false}` when the content needs the width from the start.

```tsx
import { CalendarDaysIcon, HomeIcon, InboxIcon, SettingsIcon } from "@/components/icons"
import { AppShell, AppShellHeader, AppShellMain, AppShellSidebar } from "@/registry/base-nova/ui/app-shell"
import { SidebarContent, SidebarFooter, SidebarGroup, SidebarItem, SidebarMenu } from "@/registry/base-nova/ui/animated-sidebar"

export default function AppShellIconRail() {
  return (
    <AppShell variant="window" defaultOpen={false} shortcut={null} className="h-80 w-full max-w-xl">
      <AppShellHeader>
        <span className="text-ui font-semibold">Inbox</span>
      </AppShellHeader>
      <AppShellSidebar aria-label="Mail">
        <SidebarContent>
          <SidebarGroup>
            <SidebarMenu>
              <SidebarItem icon={<HomeIcon />} label="Home" />
              <SidebarItem icon={<InboxIcon />} label="Inbox" isActive />
              <SidebarItem icon={<CalendarDaysIcon />} label="Calendar" />
            </SidebarMenu>
          </SidebarGroup>
        </SidebarContent>
        <SidebarFooter>
          <SidebarMenu>
            <SidebarItem icon={<SettingsIcon />} label="Settings" />
          </SidebarMenu>
        </SidebarFooter>
      </AppShellSidebar>
      <AppShellMain>
        <div className="flex flex-col gap-2 p-6">
          {["Quarterly review", "Design sync notes", "Invoice 0142"].map((t) => (
            <div key={t} className="flex h-10 items-center rounded-lg px-3 text-ui hover:bg-secondary">
              {t}
            </div>
          ))}
        </div>
      </AppShellMain>
    </AppShell>
  )
}
```

### Header Actions

Use `open` and `onOpenChange` when other controls fold the rail.

```tsx
"use client"

import * as React from "react"

import { BellIcon, FolderIcon, HomeIcon, SearchIcon } from "@/components/icons"
import { AppShell, AppShellHeader, AppShellMain, AppShellSidebar } from "@/registry/base-nova/ui/app-shell"
import { SidebarContent, SidebarGroup, SidebarItem, SidebarMenu } from "@/registry/base-nova/ui/animated-sidebar"
import { Button } from "@/registry/base-nova/ui/button"

const TABS = ["Overview", "Activity", "Settings"]

export default function AppShellHeaderActions() {
  const [open, setOpen] = React.useState(true)
  const [tab, setTab] = React.useState("Overview")

  return (
    <AppShell variant="window" open={open} onOpenChange={setOpen} shortcut={null} className="h-80 w-full max-w-2xl">
      <AppShellHeader>
        <span className="text-ui font-semibold">Atlas</span>
        <nav aria-label="Project" className="ml-2 flex items-center gap-0.5 max-sm:hidden">
          {TABS.map((t) => (
            <Button key={t} variant={tab === t ? "secondary" : "ghost"} size="sm" aria-current={tab === t ? "page" : undefined} onClick={() => setTab(t)}>
              {t}
            </Button>
          ))}
        </nav>
        <div className="ml-auto flex items-center gap-1.5">
          <Button variant="ghost" size="icon-sm" aria-label="Search">
            <SearchIcon />
          </Button>
          <Button variant="ghost" size="icon-sm" aria-label="Notifications">
            <BellIcon />
          </Button>
        </div>
      </AppShellHeader>
      <AppShellSidebar aria-label="Projects">
        <SidebarContent>
          <SidebarGroup>
            <SidebarMenu>
              <SidebarItem icon={<HomeIcon />} label="Home" />
              <SidebarItem icon={<FolderIcon />} label="Atlas" isActive />
              <SidebarItem icon={<FolderIcon />} label="Beacon" />
            </SidebarMenu>
          </SidebarGroup>
        </SidebarContent>
      </AppShellSidebar>
      <AppShellMain>
        <div className="flex flex-col items-start gap-3 p-6">
          <h2 className="text-balance text-lg font-semibold">{tab}</h2>
          <Button variant="secondary" size="sm" onClick={() => setOpen(!open)}>
            {open ? "Collapse to rail" : "Expand sidebar"}
          </Button>
        </div>
      </AppShellMain>
    </AppShell>
  )
}
```

## Alignment

The header's leading column is exactly `--sidebar-width-icon` wide, so the trigger sits on the rail's icon column whether the sidebar is expanded or folded. Header content starts on the sidebar's label column (`--app-shell-label-inset`), so a title or logo lines up with the nav labels. Change the rail width on `AppShell` with `style={{ "--sidebar-width-icon": "4rem" }}` and both follow.

## Page and window

`variant="page"` fills the viewport: the header and the rail stick, the panel scrolls with the page and a sticky cap keeps its rounded top under the header, so start your content at least 1rem below the panel's top. `variant="window"` is a bounded frame (give it a height) whose panel scrolls on its own; the panel's radius is the frame's radius minus its 3px gap.

## Mobile

Below the `lg` breakpoint the sidebar's children move into a left drawer and `AppShellTrigger` opens it. Following a link inside the drawer closes it; disclosure rows stay open. Lead `mobileTitle` with an 18px mark so it lines up with the nav icons.

## Keyboard

⌘/Ctrl + B toggles the rail; change the key with `shortcut` or pass `null` to turn it off. The trigger sets `aria-expanded` for the rail on desktop and for the drawer on mobile.

## Related

The sidebar parts come from [Animated Sidebar](https://qinyangwang.github.io/ui/docs/animated-sidebar).

## API Reference

### AppShell

The band. Holds the sidebar state and lays out the header, sidebar and panel on one grid. Also accepts every prop of `div`.

| Prop | Type | Default | Description |
| --- | --- | --- | --- |
| `variant` | `"page" \| "window"` | `"page"` | `page` fills the viewport and sticks to it; `window` is a rounded frame whose panel scrolls inside. |
| `open` | `boolean` | — | Controlled expanded state of the rail. |
| `defaultOpen` | `boolean` | `true` | Initial expanded state when uncontrolled. |
| `onOpenChange` | `(open: boolean) => void` | — | Called when the rail expands or collapses. |
| `shortcut` | `string \| null` | `"b"` | Key that toggles the rail with ⌘/Ctrl. `null` disables it. |

| Data attribute | Description |
| --- | --- |
| `data-state` | `expanded` or `collapsed`. |
| `data-variant` | `page` or `window`. |

### AppShellHeader

The top row. Children start on the sidebar's label column. Also accepts every prop of `header`.

| Prop | Type | Default | Description |
| --- | --- | --- | --- |
| `leading` | `ReactNode` | `<AppShellTrigger />` | Content of the rail-wide leading column. `null` leaves it empty. |

### AppShellTrigger

Toggles the rail on desktop and opens the drawer below `lg`. Also accepts every prop of `button`.

| Data attribute | Description |
| --- | --- |
| `data-state` | `expanded` or `collapsed`. |

### AppShellSidebar

The rail sidebar on desktop, a left drawer below `lg`. Takes the animated sidebar's parts as children. Also accepts every prop of [Sidebar](/docs/animated-sidebar).

| Prop | Type | Default | Description |
| --- | --- | --- | --- |
| `mobileTitle` | `ReactNode` | `"Navigation"` | Title of the mobile drawer. |
| `aria-label` | `string` | `"Sidebar"` | Accessible name of the sidebar and the drawer's sidebar. |

### AppShellMain

The inset content panel. Bring your own padding. Also accepts every prop of `main`.

### useAppShell

Read the shell state inside `AppShell`. Also returns everything `useSidebar` does.

| Prop | Type | Default | Description |
| --- | --- | --- | --- |
| `variant` | `"page" \| "window"` | — | The shell variant. |
| `isMobile` | `boolean` | — | Whether the viewport is below `lg` (the sidebar is a drawer). |
| `mobileOpen` | `boolean` | — | Whether the drawer is open. |
| `setMobileOpen` | `(open: boolean) => void` | — | Open or close the drawer. |
