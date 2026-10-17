# Tab Bar

> Bottom navigation for phones, with a label under each icon.

Page: https://qinyangwang.github.io/ui/docs/tab-bar/

## Installation

```bash
npx shadcn@latest add @qinyang/tab-bar
```

Without the `@qinyang` namespace in components.json:

```bash
npx shadcn@latest add https://qinyangwang.github.io/ui/r/tab-bar.json
```

Packages: `@base-ui/react`.

Registry items it builds on: `@qinyang/theme`, `@qinyang/locale-provider`.

## Usage

```tsx
import { TabBar, TabBarItem } from "@/components/ui/tab-bar"
```

```tsx
<TabBar aria-label="App" className="fixed inset-x-0 bottom-0">
  <TabBarItem icon={<HomeIcon />} label="Home" active />
  <TabBarItem icon={<ChatIcon />} label="Chats" badge={3} />
  <TabBarItem icon={<SettingsIcon />} label="Settings" />
</TabBar>
```

## Composition

```text
TabBar
└── TabBarItem
```

## Examples

### Links

Use with your router: pass its link to `render`.

```tsx
"use client"

import { BellIcon, HomeIcon, InboxIcon, UserIcon } from "@/components/icons"
import { TabBar, TabBarItem } from "@/registry/base-nova/ui/tab-bar"

export default function TabBarLinks() {
  return (
    <div className="w-80 overflow-hidden rounded-3xl shadow-raised">
      <TabBar>
        <TabBarItem icon={<HomeIcon />} label="Home" active render={<a href="#home" />} />
        <TabBarItem icon={<InboxIcon />} label="Inbox" badge render={<a href="#inbox" />} />
        <TabBarItem icon={<BellIcon />} label="Alerts" badge={128} render={<a href="#alerts" />} />
        <TabBarItem icon={<UserIcon />} label="Profile" render={<a href="#profile" />} />
      </TabBar>
    </div>
  )
}
```

## Phones

The bar adds the bottom safe-area inset as padding, so it can sit flush with the screen edge; add `viewport-fit=cover` to the viewport meta tag for the inset to apply. Labels show under each icon, so there are no tooltips.

## Wider screens

Swap to `IconRail` from `md` up, where a column of icons with tooltips fits better.

## Accessibility

The active item gets `aria-current="page"`. The keyboard focus ring draws around the icon pill, so it never clashes with rounded screen corners. Give the `TabBar` an `aria-label` when the page has more than one navigation region.

## API Reference

### TabBar

Also accepts every prop of `nav`.

### TabBarItem

Also accepts every prop of `button (useRender)`.

| Prop | Type | Default | Description |
| --- | --- | --- | --- |
| `icon` (required) | `ReactNode` | — | Solid icon, drawn at 20px. |
| `label` (required) | `ReactNode` | — | Text under the icon; also the accessible name. |
| `active` | `boolean` | `false` | Current destination: foreground colour and `aria-current`. |
| `badge` | `number \| boolean` | — | A count (capped at 99+) or an attention dot (`true`). |
| `render` | `ReactElement` | — | Render as another element, such as a router link. |

| Data attribute | Description |
| --- | --- |
| `data-active` | Present on the active item. |
