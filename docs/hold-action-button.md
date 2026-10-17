# Hold Action Button

> Confirms a risky action by making the user press and hold.

Page: https://qinyangwang.github.io/ui/docs/hold-action-button/

## Installation

```bash
npx shadcn@latest add @qinyang/hold-action-button
```

Without the `@qinyang` namespace in components.json:

```bash
npx shadcn@latest add https://qinyangwang.github.io/ui/r/hold-action-button.json
```

Packages: `motion`.

Registry items it builds on: `@qinyang/theme`.

## Usage

```tsx
import { HoldActionButton } from "@/components/ui/hold-action-button"
```

```tsx
<HoldActionButton tone="destructive" onHoldComplete={deleteProject}>
  Hold to delete
</HoldActionButton>
```

## Examples

### Tones

Use `destructive` for irreversible actions and `success` for confirmations.

```tsx
import { HoldActionButton } from "@/registry/base-nova/ui/hold-action-button"

export default function HoldActionButtonTones() {
  return (
    <div className="flex flex-col items-center gap-3">
      <HoldActionButton tone="primary" completeLabel="Order placed">
        Hold to place order
      </HoldActionButton>
      <HoldActionButton tone="success" completeLabel="Shift confirmed">
        Hold to confirm shift
      </HoldActionButton>
      <HoldActionButton tone="destructive" completeLabel="Subscription cancelled">
        Hold to cancel subscription
      </HoldActionButton>
    </div>
  )
}
```

### Hold Duration

Use a longer `holdDuration` for riskier actions, paired with a specific `hint`.

```tsx
import { HoldActionButton } from "@/registry/base-nova/ui/hold-action-button"

export default function HoldActionButtonDuration() {
  return (
    <div className="flex flex-col items-center gap-3">
      <HoldActionButton orientation="horizontal" holdDuration={600} completeLabel="Marked as read">
        Quick hold · 0.6s
      </HoldActionButton>
      <HoldActionButton
        orientation="horizontal"
        tone="destructive"
        holdDuration={3000}
        holdingLabel="Still holding…"
        completeLabel="Account closed"
        hint="Press and hold for three seconds to close your account"
      >
        Long hold · 3s
      </HoldActionButton>
    </div>
  )
}
```

### Stay Complete

Pass `resetDelay={null}` when the completed state should stay, and react in `onHoldComplete`.

```tsx
"use client"

import * as React from "react"

import { CheckIcon } from "@/components/icons"
import { Button } from "@/registry/base-nova/ui/button"
import { HoldActionButton } from "@/registry/base-nova/ui/hold-action-button"

export default function HoldActionButtonStayComplete() {
  const [signed, setSigned] = React.useState(false)
  const [run, setRun] = React.useState(0)
  return (
    <div className="flex flex-col items-center gap-3">
      <HoldActionButton
        key={run}
        tone="success"
        resetDelay={null}
        onHoldComplete={() => setSigned(true)}
        completeLabel={
          <>
            <CheckIcon />
            Lease signed
          </>
        }
      >
        Hold to sign lease
      </HoldActionButton>
      <p className="text-sm text-muted-foreground">
        {signed ? "Signed today. A copy is on its way to your inbox." : "Not signed yet."}
      </p>
      {signed && (
        <Button
          size="sm"
          variant="ghost"
          onClick={() => {
            setSigned(false)
            setRun((n) => n + 1)
          }}
        >
          Reset
        </Button>
      )}
    </div>
  )
}
```

### Disabled

```tsx
import { HoldActionButton } from "@/registry/base-nova/ui/hold-action-button"

export default function HoldActionButtonDisabled() {
  return (
    <HoldActionButton disabled tone="destructive">
      Hold to delete (owner only)
    </HoldActionButton>
  )
}
```

## Keyboard

Hold `Space` or `Enter` to fill; releasing early, blurring or dragging the pointer off the button drains it. `hint` is linked with `aria-describedby` and completion is announced in a live region.

## Motion

With reduced motion the wave stops moving, the press scale is removed and labels cross-fade instead of sliding.

## API Reference

### HoldActionButton

Button that confirms once it is pressed and held. Also accepts every prop of `button`.

| Prop | Type | Default | Description |
| --- | --- | --- | --- |
| `children` (required) | `ReactNode` | — | Idle label. |
| `orientation` | `"vertical" \| "horizontal"` | `"vertical"` | Liquid rises bottom→top or fills left→right. |
| `tone` | `"primary" \| "destructive" \| "success"` | `"primary"` | Fill colour. |
| `holdingLabel` | `ReactNode` | `"Keep holding"` | Label while holding. |
| `completeLabel` | `ReactNode` | `"Done"` | Label once complete. |
| `holdDuration` | `number` | `1500` | Milliseconds the hold must last. |
| `resetDelay` | `number \| null` | `1800` | Milliseconds the completed state shows before draining. `null` stays complete. |
| `onHoldComplete` | `() => void` | — | Called when the hold completes. |
| `hint` | `string` | `"Press and hold to confirm"` | Screen-reader instruction for how to use the control. |
| `disabled` | `boolean` | `false` | Disable the button. |

| Data attribute | Description |
| --- | --- |
| `data-phase` | "idle", "holding" or "complete". |
| `data-orientation` | The `orientation` value. |
