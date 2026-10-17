# Slide Action Button

> Confirms an action when the user slides it to the end.

Page: https://qinyangwang.github.io/ui/docs/slide-action-button/

## Installation

```bash
npx shadcn@latest add @qinyang/slide-action-button
```

Without the `@qinyang` namespace in components.json:

```bash
npx shadcn@latest add https://qinyangwang.github.io/ui/r/slide-action-button.json
```

Packages: `motion`.

Registry items it builds on: `@qinyang/theme`, `@qinyang/icons`, `@qinyang/text-shimmer`.

## Usage

```tsx
import { SlideActionButton } from "@/components/ui/slide-action-button"
```

```tsx
<SlideActionButton onComplete={pay}>Slide to pay</SlideActionButton>
```

## Examples

### Async

Use when confirming starts async work, returning a promise from `onComplete`.

```tsx
"use client"

import * as React from "react"

import { SlideActionButton } from "@/registry/base-nova/ui/slide-action-button"

export default function SlideActionButtonAsync() {
  const attempts = React.useRef(0)
  const [note, setNote] = React.useState("The first attempt fails on purpose.")
  return (
    <div className="flex flex-col items-center gap-3">
      <SlideActionButton
        pendingLabel="Contacting bank"
        completeLabel="Transfer sent"
        onComplete={() =>
          new Promise<void>((resolve, reject) => {
            const fail = attempts.current++ % 2 === 0
            setTimeout(() => {
              setNote(fail ? "Bank declined. The thumb sprang back; try again." : "Sent. Resets in 2 seconds.")
              if (fail) reject(new Error("declined"))
              else resolve()
            }, 1200)
          })
        }
      >
        Slide to send $250
      </SlideActionButton>
      <p className="text-sm text-muted-foreground">{note}</p>
    </div>
  )
}
```

### Threshold

Use a lower `threshold` on long tracks or for low-risk actions.

```tsx
import { SlideActionButton } from "@/registry/base-nova/ui/slide-action-button"

export default function SlideActionButtonThreshold() {
  return (
    <div className="flex flex-col items-center gap-3">
      <SlideActionButton threshold={0.5} completeLabel="Checked in">
        Slide halfway to check in
      </SlideActionButton>
      <SlideActionButton threshold={0.98} completeLabel="Vault opened">
        Slide all the way to open
      </SlideActionButton>
    </div>
  )
}
```

### Stay Complete

Use for one-time actions whose confirmed state should stay.

```tsx
"use client"

import * as React from "react"

import { LockIcon } from "@/components/icons"
import { SlideActionButton } from "@/registry/base-nova/ui/slide-action-button"

export default function SlideActionButtonStayComplete() {
  const [armed, setArmed] = React.useState(false)
  return (
    <div className="flex flex-col items-center gap-3">
      <SlideActionButton
        resetDelay={null}
        thumbIcon={<LockIcon />}
        completeLabel="Alarm armed"
        aria-label="Slide to arm the alarm"
        onComplete={() => setArmed(true)}
      >
        Slide to arm
      </SlideActionButton>
      <p className="text-sm text-muted-foreground">{armed ? "Home is armed. Sensors are watching." : "Alarm is off."}</p>
    </div>
  )
}
```

### Disabled

```tsx
import { SlideActionButton } from "@/registry/base-nova/ui/slide-action-button"

export default function SlideActionButtonDisabled() {
  return <SlideActionButton disabled>Slide to pay (add a card first)</SlideActionButton>
}
```

## Keyboard

The thumb is a `role="slider"`. `ArrowRight` / `ArrowUp` step a quarter of the track (confirming past the threshold), `ArrowLeft` / `ArrowDown` step back, `Home` or `Escape` return to the start, and `End`, `Enter` or `Space` confirm.

## Motion

The thumb uses a 420 / 34 spring and the idle label uses [Text Shimmer](https://qinyangwang.github.io/ui/docs/text-shimmer). With reduced motion springs become 200ms tweens and labels cross-fade.

## API Reference

### SlideActionButton

Drag-to-confirm track with a draggable thumb. Width defaults to 288px; set `className="w-full"` to fill.

| Prop | Type | Default | Description |
| --- | --- | --- | --- |
| `children` (required) | `ReactNode` | — | Track label, e.g. "Slide to pay". |
| `completeLabel` | `ReactNode` | `"Confirmed"` | Shown once the slide confirms. |
| `pendingLabel` | `ReactNode` | `"Processing"` | Shown while a promise returned from `onComplete` is pending. |
| `onComplete` | `() => void \| Promise<unknown>` | — | Fires when the thumb reaches the end. A rejection resets the thumb. |
| `threshold` | `number` | `0.9` | Fraction of the track to pass to confirm on release. |
| `resetDelay` | `number \| null` | `2000` | Milliseconds the completed state shows before resetting. `null` stays complete. |
| `aria-label` | `string` | `children if a string, else "Slide to confirm"` | Accessible name for the thumb. |
| `disabled` | `boolean` | `false` | Disable dragging and keyboard input. |
| `thumbIcon` | `ReactNode` | `<ChevronRightIcon />` | Icon on the idle thumb. |
| `className` | `string` | — | Classes for the track. |

| Data attribute | Description |
| --- | --- |
| `data-phase` | "idle", "pending" or "complete". |
| `data-disabled` | Present when disabled. |
